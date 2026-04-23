# RBAC 权限体系

## 概述

Skill Market 采用基于角色的访问控制 (RBAC) 模型，实现细粒度的权限管理。本文档介绍权限体系的设计原理、角色定义和使用方式。

---

## 1. 权限模型

### 1.1 核心概念

```
┌─────────┐     ┌─────────┐     ┌─────────────┐
│  User   │ n:n │  Role   │ n:n │ Permission  │
│  用户   │────▶│  角色   │────▶│    权限     │
└─────────┘     └─────────┘     └─────────────┘
     │
     │ belongs_to
     ▼
┌─────────┐
│ Tenant  │
│  租户   │
└─────────┘
```

### 1.2 权限格式

权限采用 `resource:action` 格式：

```
skill:create      # 创建 Skill
skill:read        # 查看 Skill
skill:update      # 更新 Skill
skill:delete      # 删除 Skill
skill:review      # 审核 Skill
skill:publish     # 发布 Skill
```

### 1.3 权限范围

| 范围 | 说明 | 示例 |
|-----|------|------|
| `own` | 仅自己的资源 | 普通用户只能管理自己创建的 Skill |
| `tenant` | 本租户的资源 | 租户管理员可管理租户内所有资源 |
| `global` | 全局资源 | 平台管理员可管理所有资源 |

---

## 2. 角色定义

### 2.1 系统角色

| 角色 | 代码 | 层级 | 说明 |
|-----|------|------|------|
| 超级管理员 | `super_admin` | 平台 | 最高权限，可管理所有资源 |
| 平台管理员 | `platform_admin` | 平台 | 平台级管理，可管理租户 |
| 平台运营 | `platform_operator` | 平台 | 平台级运营，Skill 审核 |
| 租户管理员 | `tenant_admin` | 租户 | 租户级管理，可管理租户内资源 |
| 租户运营 | `tenant_operator` | 租户 | 租户级运营，Skill 审核 |
| 开发者 | `developer` | 租户 | 可创建和管理 Skill |
| 龙虾管理员 | `lobster_admin` | 租户 | 可管理龙虾实例 |
| 龙虾用户 | `lobster_user` | 租户 | 可使用分配的龙虾 |
| 审计员 | `auditor` | 租户 | 只读审计权限 |
| 普通用户 | `user` | 租户 | 基础使用权限 |

### 2.2 角色权限矩阵

| 权限 | super_admin | platform_admin | tenant_admin | developer | user |
|-----|:-----------:|:--------------:|:------------:|:---------:|:----:|
| user:* | ✓ | ✓ | ✓(tenant) | - | - |
| tenant:* | ✓ | ✓ | ✓(own) | - | - |
| skill:create | ✓ | ✓ | ✓ | ✓ | - |
| skill:read | ✓ | ✓ | ✓ | ✓ | ✓ |
| skill:update | ✓ | ✓ | ✓ | ✓(own) | - |
| skill:delete | ✓ | ✓ | ✓ | ✓(own) | - |
| skill:review | ✓ | ✓ | ✓ | - | - |
| skill:publish | ✓ | ✓ | ✓ | - | - |
| lobster:* | ✓ | ✓ | ✓ | - | - |
| role:* | ✓ | ✓ | ✓(tenant) | - | - |
| audit:read | ✓ | ✓ | ✓ | - | - |

---

## 3. 技术实现

### 3.1 数据库表结构

```sql
-- 角色表
CREATE TABLE roles (
  id CHAR(36) PRIMARY KEY,
  name VARCHAR(50) NOT NULL UNIQUE,
  display_name VARCHAR(100),
  description TEXT,
  is_system BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 权限表
CREATE TABLE permissions (
  id CHAR(36) PRIMARY KEY,
  resource VARCHAR(50) NOT NULL,
  action VARCHAR(50) NOT NULL,
  description TEXT,
  UNIQUE KEY (resource, action)
);

-- 角色-权限关联
CREATE TABLE role_permissions (
  role_id CHAR(36),
  permission_id CHAR(36),
  PRIMARY KEY (role_id, permission_id),
  FOREIGN KEY (role_id) REFERENCES roles(id),
  FOREIGN KEY (permission_id) REFERENCES permissions(id)
);

-- 用户-角色关联
CREATE TABLE user_roles (
  user_id CHAR(36),
  role_id CHAR(36),
  tenant_id CHAR(36),
  PRIMARY KEY (user_id, role_id, tenant_id),
  FOREIGN KEY (user_id) REFERENCES users(id),
  FOREIGN KEY (role_id) REFERENCES roles(id),
  FOREIGN KEY (tenant_id) REFERENCES tenants(id)
);
```

### 3.2 NestJS Guard 实现

```typescript
// rbac.guard.ts
@Injectable()
export class RbacGuard implements CanActivate {
  constructor(
    private reflector: Reflector,
    private rbacService: RbacService,
  ) {}

  async canActivate(context: ExecutionContext): Promise<boolean> {
    const requiredPermissions = this.reflector.get<string[]>(
      'permissions',
      context.getHandler(),
    );
    
    if (!requiredPermissions) {
      return true;
    }

    const request = context.switchToHttp().getRequest();
    const user = request.user;

    return this.rbacService.hasPermissions(
      user.id,
      requiredPermissions,
      request.params.tenantId,
    );
  }
}

// 使用示例
@Controller('skills')
export class SkillsController {
  @Post()
  @Permissions('skill:create')
  @UseGuards(JwtAuthGuard, RbacGuard)
  create(@Body() dto: CreateSkillDto) {
    // ...
  }
}
```

### 3.3 权限检查服务

```typescript
// rbac.service.ts
@Injectable()
export class RbacService {
  async hasPermissions(
    userId: string,
    requiredPermissions: string[],
    tenantId?: string,
  ): Promise<boolean> {
    // 获取用户角色
    const userRoles = await this.getUserRoles(userId, tenantId);
    
    // 获取角色权限
    const userPermissions = await this.getRolePermissions(userRoles);
    
    // 检查是否包含所需权限
    return requiredPermissions.every(perm => 
      userPermissions.includes(perm) || 
      userPermissions.includes('*:*')  // 超级权限
    );
  }
  
  async getUserRoles(userId: string, tenantId?: string): Promise<Role[]> {
    return this.userRoleRepository.find({
      where: { userId, ...(tenantId && { tenantId }) },
      relations: ['role'],
    });
  }
}
```

---

## 4. 常见场景

### 4.1 创建租户管理员

```typescript
// 1. 创建用户
const user = await userService.create({
  email: 'admin@tenant.com',
  password: '...',
  tenantId: tenantId,
});

// 2. 分配角色
await rbacService.assignRole(user.id, 'tenant_admin', tenantId);
```

### 4.2 检查资源访问权限

```typescript
// Controller 层
@Get(':id')
@UseGuards(JwtAuthGuard, RbacGuard, ResourceOwnerGuard)
async getSkill(@Param('id') id: string, @CurrentUser() user: User) {
  const skill = await this.skillService.findOne(id);
  
  // ResourceOwnerGuard 会检查：
  // 1. 用户是否有 skill:read 权限
  // 2. 如果只有 own 范围，检查是否是创建者
  // 3. 如果是 tenant 范围，检查是否同租户
  
  return skill;
}
```

### 4.3 动态权限分配

```typescript
// 管理员为用户分配额外权限
@Post('users/:userId/permissions')
@Permissions('role:assign')
async assignPermission(
  @Param('userId') userId: string,
  @Body() dto: AssignPermissionDto,
) {
  // 检查操作者权限层级是否足够
  await this.rbacService.validateAssignment(
    currentUser,
    userId,
    dto.roleId,
  );
  
  return this.rbacService.assignRole(userId, dto.roleId, dto.tenantId);
}
```

---

## 5. 权限继承

### 5.1 层级继承

```
super_admin
    ├── platform_admin
    │       ├── platform_operator
    │       └── tenant_admin
    │               ├── tenant_operator
    │               ├── developer
    │               ├── lobster_admin
    │               │       └── lobster_user
    │               └── auditor
    └── user
```

### 5.2 权限合并

用户可以拥有多个角色，权限取并集：

```typescript
// 用户同时是 developer 和 lobster_admin
const permissions = await rbacService.getMergedPermissions(userId, tenantId);
// 结果：developer 权限 ∪ lobster_admin 权限
```

---

## 6. 安全考虑

### 6.1 权限缓存

```typescript
// 使用 Redis 缓存用户权限
const cacheKey = `user:${userId}:permissions:${tenantId}`;
const cached = await redis.get(cacheKey);

if (!cached) {
  const permissions = await computePermissions(userId, tenantId);
  await redis.setex(cacheKey, 300, JSON.stringify(permissions));
  return permissions;
}

return JSON.parse(cached);
```

### 6.2 权限变更同步

```typescript
// 角色/权限变更时清除缓存
@OnEvent('role.updated')
async handleRoleUpdate(event: RoleUpdatedEvent) {
  // 获取所有拥有此角色的用户
  const users = await this.getUsersByRole(event.roleId);
  
  // 清除相关用户的权限缓存
  for (const user of users) {
    await this.clearPermissionCache(user.id);
  }
}
```

### 6.3 越权防护

```typescript
// 防止越权操作
async assignRole(
  operatorId: string,
  targetUserId: string,
  roleId: string,
  tenantId: string,
) {
  const operatorLevel = await this.getUserLevel(operatorId);
  const targetRoleLevel = await this.getRoleLevel(roleId);
  
  // 操作者不能分配高于或等于自己级别的角色
  if (targetRoleLevel >= operatorLevel) {
    throw new ForbiddenException('Cannot assign role with equal or higher level');
  }
}
```

---

## 7. API 权限清单

### 7.1 用户管理

| API | 权限 | 说明 |
|-----|------|------|
| `GET /users` | `user:read` | 查看用户列表 |
| `POST /users` | `user:create` | 创建用户 |
| `PUT /users/:id` | `user:update` | 更新用户 |
| `DELETE /users/:id` | `user:delete` | 删除用户 |

### 7.2 Skill 管理

| API | 权限 | 说明 |
|-----|------|------|
| `GET /skills` | `skill:read` | 查看 Skill 列表 |
| `POST /skills` | `skill:create` | 创建 Skill |
| `PUT /skills/:id` | `skill:update` | 更新 Skill |
| `DELETE /skills/:id` | `skill:delete` | 删除 Skill |
| `POST /skills/:id/submit` | `skill:submit` | 提交审核 |
| `POST /skills/:id/review` | `skill:review` | 审核 Skill |
| `POST /skills/:id/publish` | `skill:publish` | 发布 Skill |

### 7.3 租户管理

| API | 权限 | 说明 |
|-----|------|------|
| `GET /tenants` | `tenant:read` | 查看租户列表 |
| `POST /tenants` | `tenant:create` | 创建租户 |
| `PUT /tenants/:id` | `tenant:update` | 更新租户 |
| `DELETE /tenants/:id` | `tenant:delete` | 删除租户 |

---

## 8. 排障指南

### 8.1 权限不足问题

**现象**：用户操作时返回 403 Forbidden

**排查步骤**：
1. 确认用户角色
   ```sql
   SELECT r.name FROM user_roles ur
   JOIN roles r ON ur.role_id = r.id
   WHERE ur.user_id = '<user_id>';
   ```

2. 确认角色权限
   ```sql
   SELECT p.resource, p.action FROM role_permissions rp
   JOIN permissions p ON rp.permission_id = p.id
   WHERE rp.role_id = '<role_id>';
   ```

3. 检查 API 所需权限
   - 查看 Controller 上的 `@Permissions()` 装饰器

4. 检查资源范围
   - own/tenant/global 范围是否匹配

### 8.2 权限缓存问题

**现象**：角色变更后权限未生效

**解决**：
```bash
# 清除 Redis 中的权限缓存
redis-cli KEYS "user:*:permissions:*" | xargs redis-cli DEL
```

---

## 相关文档

- [系统架构](/internalDocs/background/architecture.md)
- [后端错误码](/internalDocs/error-codes/backend-errors.md)
- [后端排障](/internalDocs/playbooks/backend/common-issues-triage.md)
