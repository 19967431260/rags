# 后端服务错误码参考

## 概述

本文档整理了 skill-market 后端服务（NestJS）中的所有错误码和错误消息，按模块分类，便于技术支持快速定位问题。

---

## 1. 通用错误码

### HTTP 状态码映射

| 状态码 | 含义 | 常见原因 |
|-------|------|---------|
| 400 | Bad Request | 请求参数校验失败 |
| 401 | Unauthorized | Token 无效或过期 |
| 403 | Forbidden | 权限不足 |
| 404 | Not Found | 资源不存在 |
| 409 | Conflict | 资源冲突（如重复创建） |
| 422 | Unprocessable Entity | 业务逻辑校验失败 |
| 500 | Internal Server Error | 服务器内部错误 |
| 503 | Service Unavailable | 服务暂不可用 |

### 通用错误格式

```json
{
  "statusCode": 400,
  "message": "Validation failed",
  "error": "Bad Request",
  "details": [
    {
      "field": "name",
      "constraints": ["name should not be empty"]
    }
  ]
}
```

---

## 2. 用户模块 (Users)

### 认证相关

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Invalid credentials` | 用户名或密码错误 | 确认账号密码正确 |
| `User not found` | 用户不存在 | 检查用户 ID 或邮箱 |
| `User already exists` | 邮箱已注册 | 使用其他邮箱或找回密码 |
| `Account is disabled` | 账号被禁用 | 联系管理员启用 |
| `Email not verified` | 邮箱未验证 | 检查邮箱验证链接 |

### Token 相关

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Token expired` | Token 已过期 | 重新登录获取新 Token |
| `Invalid token` | Token 格式错误或被篡改 | 重新登录 |
| `Token not provided` | 未携带 Authorization 头 | 添加 Bearer Token |
| `Refresh token expired` | 刷新 Token 过期 | 重新登录 |

### 用户管理

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Cannot delete yourself` | 用户试图删除自己 | 联系其他管理员操作 |
| `Cannot modify super admin` | 试图修改超管权限 | 超管权限不可修改 |
| `Password too weak` | 密码强度不足 | 使用更复杂的密码 |
| `Old password incorrect` | 修改密码时旧密码错误 | 确认旧密码正确 |

---

## 3. 租户模块 (Tenants)

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Tenant not found` | 租户不存在 | 检查租户 ID |
| `Tenant name already exists` | 租户名称重复 | 使用其他名称 |
| `Tenant is disabled` | 租户被禁用 | 联系平台管理员 |
| `Tenant quota exceeded` | 超出租户配额 | 升级套餐或清理资源 |
| `Cannot delete tenant with users` | 租户下有用户 | 先删除或迁移用户 |
| `Cannot delete tenant with skills` | 租户下有 Skill | 先删除或迁移 Skill |

### 租户配额错误

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `User quota exceeded` | 用户数超限 | 删除用户或提升配额 |
| `Skill quota exceeded` | Skill 数超限 | 删除 Skill 或提升配额 |
| `Storage quota exceeded` | 存储空间超限 | 清理文件或提升配额 |

---

## 4. Skill 模块 (Skills)

### 基础操作

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Skill not found` | Skill 不存在 | 检查 Skill ID |
| `Skill name already exists` | 同租户下名称重复 | 修改 Skill 名称 |
| `Invalid skill type` | skillType 不在枚举范围 | 使用 `mcp` 或 `prompt` |
| `Skill is not editable` | 非 draft 状态不可编辑 | 先撤回到 draft 状态 |

### 状态流转

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Invalid status transition` | 状态转换不合法 | 参考状态机设计 |
| `Skill must be approved before publish` | 未审核通过就发布 | 先完成审核流程 |
| `Cannot delete published skill` | 删除已发布 Skill | 先下架再删除 |
| `Skill already submitted for review` | 重复提交审核 | 等待审核结果 |

**Skill 状态流转图：**
```
draft -> pending_review -> approved -> published -> deprecated
                       \-> rejected -> draft
```

### 审核相关

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `No permission to review` | 无审核权限 | 需要 operator 角色 |
| `Cannot review own skill` | 审核自己的 Skill | 由其他人审核 |
| `Review comment required for rejection` | 拒绝时未填原因 | 填写拒绝原因 |

### 版本相关

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Version not found` | 版本不存在 | 检查版本 ID |
| `Cannot delete current version` | 删除正在使用的版本 | 先切换到其他版本 |
| `Version already exists` | 版本号重复 | 使用新版本号 |

---

## 5. 龙虾实例模块 (Lobster Instances)

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Instance not found` | 实例不存在 | 检查实例 ID |
| `Instance already exists` | 机器 ID 重复 | 检查是否重复注册 |
| `Instance is offline` | 实例离线 | 检查 Agent 状态 |
| `Cannot delete online instance` | 删除在线实例 | 先使实例离线 |

### 绑定相关

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Skill already bound` | Skill 已绑定到该实例 | 无需重复绑定 |
| `Skill not bound` | 解绑不存在的绑定 | 检查绑定关系 |
| `Instance quota exceeded` | 实例绑定 Skill 数超限 | 解绑部分 Skill |

---

## 6. Agent 模块

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Agent not found` | Agent 不存在 | 检查 Agent ID |
| `Agent registration failed` | 注册失败 | 检查签名和时间同步 |
| `Agent already registered` | 重复注册 | 清理旧配置后重试 |
| `Invalid agent signature` | 签名验证失败 | 检查系统时间 |
| `Agent heartbeat timeout` | 心跳超时 | 检查网络连接 |

---

## 7. 文件上传模块

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `File too large` | 文件超过大小限制 | 压缩或分片上传 |
| `Invalid file type` | 文件类型不允许 | 使用允许的文件类型 |
| `Upload failed` | 上传过程出错 | 重试或检查网络 |
| `File not found` | 文件不存在 | 检查文件路径 |

**文件大小限制：**
- 图片：5MB
- 文档：20MB
- Skill 包：100MB

**允许的文件类型：**
- 图片：`jpg`, `jpeg`, `png`, `gif`, `webp`
- 文档：`pdf`, `doc`, `docx`, `md`
- Skill 包：`zip`, `tar.gz`

---

## 8. 权限模块 (RBAC)

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Permission denied` | 无操作权限 | 检查角色权限 |
| `Role not found` | 角色不存在 | 检查角色 ID |
| `Cannot delete default role` | 删除系统角色 | 系统角色不可删除 |
| `User already has this role` | 重复分配角色 | 无需重复分配 |

### 系统角色列表

| 角色 | 权限范围 | 说明 |
|-----|---------|------|
| `super_admin` | 全部权限 | 平台超级管理员 |
| `platform_admin` | 平台管理 | 平台管理员 |
| `tenant_admin` | 租户管理 | 租户管理员 |
| `operator` | 运营操作 | 运营人员 |
| `developer` | 开发相关 | 开发者 |
| `user` | 基础使用 | 普通用户 |

---

## 9. 行为安全模块

| 错误消息 | 触发场景 | 解决方案 |
|---------|---------|---------|
| `Invalid callback signature` | 回调签名验证失败 | 检查签名算法 |
| `Event not found` | 安全事件不存在 | 检查事件 ID |
| `Invalid event type` | 事件类型不合法 | 使用允许的类型 |

---

## 10. 数据库错误

### TypeORM 错误

| 错误码 | 含义 | 解决方案 |
|-------|------|---------|
| `ER_DUP_ENTRY` | 唯一键冲突 | 检查重复数据 |
| `ER_NO_REFERENCED_ROW` | 外键约束失败 | 检查关联数据存在 |
| `ER_ROW_IS_REFERENCED` | 数据被引用无法删除 | 先删除关联数据 |
| `ER_LOCK_WAIT_TIMEOUT` | 锁等待超时 | 检查并发操作 |
| `ER_DATA_TOO_LONG` | 数据超过字段长度 | 检查字段长度限制 |

### 连接错误

| 错误码 | 含义 | 解决方案 |
|-------|------|---------|
| `ECONNREFUSED` | 连接被拒绝 | 检查数据库服务 |
| `ETIMEDOUT` | 连接超时 | 检查网络和防火墙 |
| `ER_ACCESS_DENIED` | 认证失败 | 检查用户名密码 |

---

## 11. 校验错误详解

### class-validator 错误

| 装饰器 | 错误消息示例 | 说明 |
|-------|------------|------|
| `@IsNotEmpty()` | `xxx should not be empty` | 字段不能为空 |
| `@IsString()` | `xxx must be a string` | 必须是字符串 |
| `@IsNumber()` | `xxx must be a number` | 必须是数字 |
| `@IsEmail()` | `xxx must be an email` | 必须是邮箱格式 |
| `@IsEnum()` | `xxx must be a valid enum value` | 必须是枚举值 |
| `@MinLength(n)` | `xxx must be longer than n characters` | 最小长度 |
| `@MaxLength(n)` | `xxx must be shorter than n characters` | 最大长度 |
| `@IsUUID()` | `xxx must be a UUID` | 必须是 UUID 格式 |
| `@IsArray()` | `xxx must be an array` | 必须是数组 |

---

## 快速排查指南

### 根据状态码定位

```
400 → 检查请求参数格式和校验规则
401 → 检查 Token 是否有效
403 → 检查用户角色和权限
404 → 检查资源是否存在
409 → 检查是否有数据冲突
422 → 检查业务逻辑约束
500 → 查看后端日志定位具体错误
```

### 根据错误消息定位

```bash
# 在后端代码中搜索错误消息
grep -r "错误消息关键字" backend/src/

# 查看对应的 Service 逻辑
# backend/src/<module>/<module>.service.ts
```

---

## 相关文档

- [后端排障手册](/internalDocs/playbooks/backend/common-issues-triage.md)
- [RBAC 权限设计](/docs/guides/rbac-design.md)
- [Skill 状态机](/docs/guides/skill-status-machine.md)
