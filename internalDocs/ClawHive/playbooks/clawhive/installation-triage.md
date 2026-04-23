# ClawHive 安装与启动问题排障手册

## 概述

本手册用于排查 ClawHive 桌面客户端（Electron 应用）的安装、启动、登录和基础功能问题。

---

## 1. 安装失败

### 现象
- 安装包下载后无法安装
- 安装过程中报错退出
- 安装完成但无法启动

### 排查步骤

#### macOS

1. **检查系统要求**
   - macOS 10.13 或更高版本
   - 至少 500MB 可用磁盘空间

2. **检查安装包完整性**
   ```bash
   # 检查 DMG 文件
   hdiutil verify /path/to/ClawHive.dmg
   ```

3. **检查 Gatekeeper 设置**
   ```bash
   # 如果提示"无法验证开发者"
   sudo spctl --master-disable  # 临时允许任何来源（谨慎使用）
   ```

4. **检查应用签名**
   ```bash
   codesign -dv --verbose=4 /Applications/ClawHive.app
   ```

#### Windows

1. **检查系统要求**
   - Windows 10 1903 或更高版本
   - 至少 500MB 可用磁盘空间
   - 需要管理员权限

2. **检查安装日志**
   ```
   %TEMP%\ClawHive-Setup-*.log
   ```

3. **检查杀毒软件**
   - 部分杀毒软件可能误报 Electron 应用
   - 添加安装目录到白名单

### 常见原因
| 错误信息 | 原因 | 解决方案 |
|---------|------|---------|
| `ENOSPC` | 磁盘空间不足 | 清理磁盘空间 |
| `Code signature invalid` | 签名验证失败 | 重新下载安装包 |
| `被杀毒软件拦截` | 误报 | 添加白名单 |

---

## 2. 启动失败

### 现象
- 双击图标无反应
- 启动后立即崩溃
- 卡在启动界面

### 排查步骤

1. **检查进程状态**
   ```bash
   # macOS
   ps aux | grep -i clawhive
   
   # Windows (PowerShell)
   Get-Process | Where-Object {$_.Name -like "*clawhive*"}
   ```

2. **检查日志文件**
   ```bash
   # macOS
   cat ~/Library/Logs/ClawHive/main.log
   
   # Windows
   type %USERPROFILE%\AppData\Roaming\ClawHive\logs\main.log
   ```

3. **检查端口占用**
   - ClawHive 本地服务使用特定端口
   ```bash
   # macOS
   lsof -i :15234
   
   # Windows
   netstat -ano | findstr :15234
   ```

4. **清理缓存重试**
   ```bash
   # macOS
   rm -rf ~/Library/Application\ Support/ClawHive/Cache
   rm -rf ~/Library/Application\ Support/ClawHive/GPUCache
   
   # Windows
   rmdir /s /q "%APPDATA%\ClawHive\Cache"
   rmdir /s /q "%APPDATA%\ClawHive\GPUCache"
   ```

5. **检查系统资源**
   - 内存是否不足（建议至少 4GB 可用）
   - CPU 是否过载

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 无反应 | 进程残留 | 杀死残留进程后重启 |
| 立即崩溃 | 配置文件损坏 | 清理用户数据目录 |
| 卡在启动界面 | 网络超时 | 检查网络连接和代理设置 |

---

## 3. 登录问题

### 现象
- 登录按钮点击无效
- 登录超时
- 登录成功但页面空白

### 排查步骤

1. **检查网络连接**
   ```bash
   # 测试后端服务连通性
   curl -v https://skill-market.example.com/api/health
   ```

2. **检查 DNS 解析**
   ```bash
   nslookup skill-market.example.com
   ```

3. **检查代理设置**
   - ClawHive 会读取系统代理设置
   - 检查是否需要配置企业代理

4. **检查证书信任**
   - HTTPS 证书是否被信任
   - 企业自签名证书需要导入系统信任链

5. **查看渲染进程日志**
   ```bash
   # macOS
   cat ~/Library/Logs/ClawHive/renderer.log
   ```

6. **检查 OAuth 配置**
   - 确认后端 OAuth 回调地址配置正确
   - 检查 CORS 配置是否允许 ClawHive 域名

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 登录超时 | 网络不通 | 检查防火墙和代理 |
| OAuth 报错 | 回调配置错误 | 联系管理员检查 OAuth 配置 |
| 页面空白 | 前端资源加载失败 | 清理缓存重试 |

---

## 4. WEClawHelper Agent 问题

### 现象
- ClawHive 显示 Agent 离线
- Skill 无法同步到本地
- 执行任务无响应

### 排查步骤

1. **检查 Agent 进程**
   ```bash
   # macOS
   ps aux | grep WEClawHelper
   
   # Windows
   Get-Process | Where-Object {$_.Name -like "*WEClawHelper*"}
   ```

2. **检查 Agent 日志**
   ```bash
   # macOS
   tail -100 ~/Library/Application\ Support/WEClawHelper/logs/weclaw-helper.log
   
   # Windows
   type "%APPDATA%\WEClawHelper\logs\weclaw-helper.log"
   ```

3. **检查 Agent 配置**
   ```bash
   # macOS
   cat ~/Library/Application\ Support/WEClawHelper/config.json
   
   # Windows
   type "%APPDATA%\WEClawHelper\config.json"
   ```

4. **重启 Agent**
   ```bash
   # macOS - 通过 ClawHive 菜单重启，或手动：
   pkill -f WEClawHelper
   open /Applications/ClawHive.app  # 会自动拉起 Agent
   
   # Windows
   taskkill /IM WEClawHelper.exe /F
   # 重新打开 ClawHive
   ```

5. **检查 Agent 注册状态**
   - 在后端数据库查询
   ```sql
   SELECT * FROM agents WHERE machine_id = '<machine_id>';
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| Agent 离线 | 进程未运行 | 重启 ClawHive |
| 注册失败 | 签名验证不通过 | 检查系统时间是否同步 |
| Skill 不同步 | 心跳异常 | 检查网络和防火墙 |

---

## 5. Skill 执行问题

### 现象
- Skill 列表加载慢或为空
- Skill 执行超时
- Skill 执行结果错误

### 排查步骤

1. **检查 Skill 缓存**
   ```bash
   # macOS
   ls -la ~/Library/Application\ Support/ClawHive/skills/
   
   # Windows
   dir "%APPDATA%\ClawHive\skills\"
   ```

2. **检查 Skill 配置**
   ```bash
   # 查看已安装 Skill 的配置
   cat ~/Library/Application\ Support/ClawHive/skills/<skill_id>/manifest.json
   ```

3. **检查执行日志**
   ```bash
   # macOS
   tail -100 ~/Library/Application\ Support/ClawHive/logs/skill-execution.log
   ```

4. **检查 MCP 服务状态**
   - MCP 类型 Skill 依赖本地 MCP Server
   ```bash
   ps aux | grep mcp
   lsof -i :3000  # 检查 MCP 端口
   ```

5. **手动触发同步**
   - 在 ClawHive 设置中点击"同步 Skill"
   - 或重启应用触发全量同步

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 列表为空 | 未同步或同步失败 | 手动触发同步 |
| 执行超时 | MCP Server 未启动 | 检查并启动 MCP 服务 |
| 结果错误 | Skill 版本不匹配 | 更新到最新版本 |

---

## 6. 反馈日志收集

### 现象
- 用户需要提交问题反馈
- 技术支持需要收集日志

### 收集步骤

1. **使用内置反馈功能**
   - ClawHive 菜单 -> 帮助 -> 反馈问题
   - 会自动打包日志并上传

2. **手动收集日志**
   ```bash
   # macOS - 创建日志压缩包
   cd ~/Library/Application\ Support
   zip -r ~/Desktop/clawhive-logs.zip ClawHive/logs/ WEClawHelper/logs/
   
   # Windows
   # 压缩以下目录：
   # %APPDATA%\ClawHive\logs\
   # %APPDATA%\WEClawHelper\logs\
   ```

3. **日志文件说明**
   | 文件 | 内容 |
   |-----|------|
   | `main.log` | 主进程日志 |
   | `renderer.log` | 渲染进程日志 |
   | `skill-execution.log` | Skill 执行日志 |
   | `weclaw-helper.log` | Agent 日志 |

4. **敏感信息脱敏**
   - 日志中可能包含用户名、路径等信息
   - 提交前确认是否需要脱敏

---

## 7. 自动更新问题

### 现象
- 更新检查失败
- 下载更新包失败
- 更新安装失败

### 排查步骤

1. **检查当前版本**
   - ClawHive 菜单 -> 关于
   - 或查看 `package.json` 中的版本号

2. **检查更新服务器**
   ```bash
   curl -v https://update.skill-market.example.com/latest
   ```

3. **检查下载目录**
   ```bash
   # macOS
   ls -la ~/Library/Application\ Support/ClawHive/updates/
   
   # Windows
   dir "%APPDATA%\ClawHive\updates\"
   ```

4. **清理更新缓存**
   ```bash
   # macOS
   rm -rf ~/Library/Application\ Support/ClawHive/updates/
   
   # Windows
   rmdir /s /q "%APPDATA%\ClawHive\updates"
   ```

### 常见原因
| 现象 | 原因 | 解决方案 |
|-----|------|---------|
| 检查失败 | 更新服务器不可达 | 检查网络和代理 |
| 下载失败 | 磁盘空间不足 | 清理磁盘空间 |
| 安装失败 | 权限不足 | 使用管理员权限运行 |

---

## 相关文档

- [日志路径汇总](/docs/guides/client-log-paths.md)
- [WEClawHelper 排障](/internalDocs/playbooks/weclawhelper/connection-triage.md)
- [错误码参考](/internalDocs/error-codes/clawhive-errors.md)
