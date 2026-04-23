# Skill 开发最佳实践

## 概述

本文档整理了 Skill Market 平台上 Skill 开发的最佳实践，帮助开发者创建高质量、易维护的 Skill。

---

## 1. Skill 类型选择

### MCP 类型 Skill

**适用场景：**
- 需要执行复杂计算或逻辑
- 需要访问外部 API 或数据库
- 需要操作本地文件系统
- 需要与其他服务集成

**优点：**
- 功能强大，可实现复杂逻辑
- 支持多种编程语言
- 可复用现有代码库

**注意事项：**
- 需要管理 MCP Server 生命周期
- 需要处���错误和超时
- 注意安全性和权限控制

### Prompt 类型 Skill

**适用场景：**
- 基于 LLM 的文本处理
- 对话流程编排
- 知识问答

**优点：**
- 开发简单，无需编写代码
- 易于调试和迭代
- 可快速验证想法

**注意事项：**
- 依赖 LLM 服务的可用性
- 输出不完全可控
- 需要精心设计 Prompt

---

## 2. Skill 结构规范

### 目录结构

```
skill-name/
├── manifest.json       # Skill 元数据（必需）
├── README.md           # 使用说明（推荐）
├── src/                # 源代码目录
│   ├── index.ts        # 入口文件
│   └── ...
├── assets/             # 静态资源
│   └── icon.png        # Skill 图标
└── tests/              # 测试文件
    └── index.test.ts
```

### manifest.json 规范

```json
{
  "name": "skill-name",
  "version": "1.0.0",
  "description": "Skill 简短描述",
  "type": "mcp",
  "author": "作者名",
  "license": "MIT",
  "keywords": ["关键词1", "关键词2"],
  "main": "src/index.ts",
  "icon": "assets/icon.png",
  "dependencies": {
    "package-name": "^1.0.0"
  },
  "mcp": {
    "server": {
      "command": "node",
      "args": ["dist/server.js"]
    },
    "tools": [
      {
        "name": "tool_name",
        "description": "工具描述",
        "inputSchema": {
          "type": "object",
          "properties": {
            "param1": {
              "type": "string",
              "description": "参数说明"
            }
          },
          "required": ["param1"]
        }
      }
    ]
  }
}
```

---

## 3. MCP Skill 开发最佳实践

### 3.1 错误处理

```typescript
// 推荐：完善的错误处理
async function handleRequest(params: RequestParams): Promise<Response> {
  try {
    // 参数校验
    if (!params.input) {
      throw new Error('Missing required parameter: input');
    }
    
    // 业务逻辑
    const result = await processInput(params.input);
    
    return {
      success: true,
      data: result
    };
  } catch (error) {
    // 区分错误类型
    if (error instanceof ValidationError) {
      return {
        success: false,
        error: 'validation_error',
        message: error.message
      };
    }
    
    // 记录日志
    logger.error('Request failed', { error, params });
    
    return {
      success: false,
      error: 'internal_error',
      message: 'An unexpected error occurred'
    };
  }
}
```

### 3.2 超时处理

```typescript
// 推荐：添加超时控制
async function executeWithTimeout<T>(
  promise: Promise<T>,
  timeoutMs: number = 30000
): Promise<T> {
  const timeout = new Promise<never>((_, reject) => {
    setTimeout(() => {
      reject(new Error(`Operation timed out after ${timeoutMs}ms`));
    }, timeoutMs);
  });
  
  return Promise.race([promise, timeout]);
}

// 使用示例
const result = await executeWithTimeout(
  fetchExternalData(),
  10000  // 10 秒超时
);
```

### 3.3 资源管理

```typescript
// 推荐：正确释放资源
class SkillServer {
  private connections: Set<Connection> = new Set();
  
  async shutdown(): Promise<void> {
    // 关闭所有连接
    for (const conn of this.connections) {
      await conn.close();
    }
    this.connections.clear();
    
    // 清理临时文件
    await this.cleanupTempFiles();
    
    // 关闭数据库连接
    await this.db?.close();
  }
}

// 注册关闭钩子
process.on('SIGTERM', async () => {
  await server.shutdown();
  process.exit(0);
});
```

### 3.4 日志记录

```typescript
// 推荐：结构化日志
import { createLogger } from './logger';

const logger = createLogger('skill-name');

// 不同级别的日志
logger.debug('Processing request', { requestId, params });
logger.info('Request completed', { requestId, duration });
logger.warn('Rate limit approaching', { current, limit });
logger.error('Request failed', { requestId, error: err.message, stack: err.stack });
```

---

## 4. Prompt Skill 开发最佳实践

### 4.1 Prompt 设计原则

1. **明确角色**：清晰定义 AI 的角色和职责
2. **具体指令**：使用具体、明确的指令
3. **示例驱动**：提供输入输出示例
4. **边界约束**：明确限制和约束条件
5. **格式规范**：指定输出格式

### 4.2 Prompt 模板示例

```markdown
# 角色
你是一个专业的 {领域} 专家，负责 {任务描述}。

# 任务
根据用户输入，完成以下任务：
1. {子任务1}
2. {子任务2}

# 输入格式
用户会提供：
- {输入项1}：{说明}
- {输入项2}：{说明}

# 输出格式
请按以下 JSON 格式返回结果：
```json
{
  "field1": "value1",
  "field2": "value2"
}
```

# 示例
输入：{示例输入}
输出：{示例输出}

# 注意事项
- {注意事项1}
- {注意事项2}

# 约束
- 禁止 {禁止行为}
- 必须 {必须行为}
```

### 4.3 变量使用

```markdown
# 支持的变量语法
{{user_input}}      # 用户输入
{{context}}         # 上下文信息
{{current_time}}    # 当前时间
{{user_name}}       # 用户名称

# 示例
请帮助 {{user_name}} 完成以下任务：
{{user_input}}

当前时间：{{current_time}}
```

---

## 5. 安全最佳实践

### 5.1 输入校验

```typescript
// 推荐：严格的输入校验
import { z } from 'zod';

const InputSchema = z.object({
  url: z.string().url(),
  timeout: z.number().min(1000).max(60000).default(10000),
  headers: z.record(z.string()).optional()
});

function validateInput(input: unknown) {
  const result = InputSchema.safeParse(input);
  if (!result.success) {
    throw new ValidationError(result.error.message);
  }
  return result.data;
}
```

### 5.2 敏感信息处理

```typescript
// 推荐：不在日志中记录敏感信息
function sanitizeForLogging(params: any): any {
  const sensitive = ['password', 'token', 'secret', 'apiKey'];
  const sanitized = { ...params };
  
  for (const key of sensitive) {
    if (key in sanitized) {
      sanitized[key] = '***REDACTED***';
    }
  }
  
  return sanitized;
}

logger.info('Request received', sanitizeForLogging(params));
```

### 5.3 命令注入防护

```typescript
// 不推荐：直接拼接命令
const cmd = `ls ${userInput}`;  // 危险！

// 推荐：使用参数化
import { execFile } from 'child_process';

execFile('ls', [sanitizedPath], (error, stdout) => {
  // 安全执行
});
```

### 5.4 文件路径校验

```typescript
import path from 'path';

// 推荐：防止路径遍历攻击
function validatePath(userPath: string, baseDir: string): string {
  const resolved = path.resolve(baseDir, userPath);
  
  // 确保路径在允许的目录内
  if (!resolved.startsWith(baseDir)) {
    throw new Error('Invalid path: path traversal detected');
  }
  
  return resolved;
}
```

---

## 6. 性能优化

### 6.1 缓存使用

```typescript
// 推荐：合理使用缓存
import LRU from 'lru-cache';

const cache = new LRU<string, any>({
  max: 1000,           // 最多缓存 1000 项
  ttl: 1000 * 60 * 5,  // 5 分钟过期
});

async function getData(key: string): Promise<any> {
  // 先查缓存
  const cached = cache.get(key);
  if (cached) {
    return cached;
  }
  
  // 缓存未命中，从源获取
  const data = await fetchFromSource(key);
  cache.set(key, data);
  
  return data;
}
```

### 6.2 并发控制

```typescript
// 推荐：限制并发数
import pLimit from 'p-limit';

const limit = pLimit(5);  // 最多 5 个并发

async function processItems(items: string[]): Promise<void> {
  await Promise.all(
    items.map(item => limit(() => processItem(item)))
  );
}
```

### 6.3 流式处理

```typescript
// 推荐：大数据量使用流式处理
import { createReadStream, createWriteStream } from 'fs';
import { pipeline } from 'stream/promises';

async function processLargeFile(input: string, output: string): Promise<void> {
  await pipeline(
    createReadStream(input),
    transformStream,
    createWriteStream(output)
  );
}
```

---

## 7. 测试实践

### 7.1 单元测试

```typescript
// 推荐：完善的单元测试
import { describe, it, expect } from 'vitest';

describe('processInput', () => {
  it('should handle valid input', async () => {
    const result = await processInput({ text: 'hello' });
    expect(result.success).toBe(true);
    expect(result.data).toBeDefined();
  });
  
  it('should reject empty input', async () => {
    await expect(processInput({ text: '' }))
      .rejects.toThrow('Input cannot be empty');
  });
  
  it('should handle timeout', async () => {
    // 模拟超时场景
    jest.useFakeTimers();
    const promise = processInput({ text: 'slow' });
    jest.advanceTimersByTime(30001);
    await expect(promise).rejects.toThrow('timeout');
  });
});
```

### 7.2 集成测试

```typescript
// 推荐：MCP Server 集成测试
describe('MCP Server Integration', () => {
  let server: MCPServer;
  
  beforeAll(async () => {
    server = await startServer();
  });
  
  afterAll(async () => {
    await server.close();
  });
  
  it('should respond to tool call', async () => {
    const response = await server.handleToolCall({
      name: 'my_tool',
      arguments: { param1: 'value1' }
    });
    
    expect(response.success).toBe(true);
  });
});
```

---

## 8. 版本管理

### 8.1 语义化版本

遵循 [Semantic Versioning](https://semver.org/)：
- **MAJOR**：不兼容的 API 变更
- **MINOR**：向后兼容的功能新增
- **PATCH**：向后兼容的问题修复

### 8.2 变更日志

```markdown
# Changelog

## [1.2.0] - 2024-01-15

### Added
- 新增 xxx 功能

### Changed
- 优化 xxx 性能

### Fixed
- 修复 xxx 问题

### Deprecated
- xxx 将在下个大版本移除
```

---

## 9. 文档规范

### 9.1 README 模板

```markdown
# Skill 名称

简短描述这个 Skill 做什么。

## 功能特性

- 特性 1
- 特性 2

## 安装

说明如何安装这个 Skill。

## 使用方法

### 基础用法

示例代码或操作步骤。

### 高级用法

更复杂的使用场景。

## 配置选项

| 选项 | 类型 | 默认值 | 说明 |
|-----|------|-------|------|
| option1 | string | - | 说明 |

## 常见问题

### Q: 问题1？
A: 答案1。

## 更新日志

见 CHANGELOG.md

## 许可证

MIT
```

---

## 相关文档

- [Skill 状态机](/docs/guides/skill-status-machine.md)
- [Skill 管理排障](/internalDocs/playbooks/backend/skill-management-triage.md)
- [后端错误码](/internalDocs/error-codes/backend-errors.md)
