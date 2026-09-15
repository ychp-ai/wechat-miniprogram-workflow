# 关联技能清单

本工作流直接关联下列 16 个 Skill。它们不是本仓库内置内容，也不是全部必装或必读；按入口映射和任务需求读取。身份、数据库、动画等分类不会自动改变用户项目技术栈。

## 直接关联

| Skill 精确名称 | 职责 | 使用条件 |
|---|---|---|
| `ui-ux-pro-max` | 页面布局、视觉和交互规范 | 设计、改版或界面打磨 |
| `frontend-design` | 页面视觉创意与实现指导 | 需要视觉方向时；建议适配小程序 |
| `impeccable` | 界面审查和打磨 | 页面改版或局部优化 |
| `miniprogram-development` | 工程、实现、验证、预览与上传 | 对应小程序开发操作 |
| `auth-wechat-miniprogram` | CloudBase 原生身份 | 使用 CloudBase 身份能力 |
| `cloud-functions` | CloudBase 云函数 | 开发或调试云函数 |
| `cloudbase-document-database-in-wechat-miniprogram` | 小程序客户端文档数据库 | 使用 wx.cloud.database 的操作 |
| `cloudbase-code-review` | CloudBase 代码与权限检查 | CloudBase 相关审查 |
| `ai-model-wechat` | 小程序 AI 接入 | 用户明确要求 AI 能力 |
| `skyline-overview` | Skyline 选型和总体说明 | 评估或搭建 Skyline 项目 |
| `skyline-config` | Skyline 配置 | 已决定使用 Skyline |
| `skyline-components` | Skyline 组件约束 | Skyline 页面或组件开发 |
| `skyline-wxss` | Skyline 样式兼容 | Skyline 页面样式 |
| `skyline-worklet` | 手势与动画 | Skyline 动效 |
| `skyline-route` | 页面转场 | Skyline 转场 |
| `skyline-scroll-api` | 滚动交互 | Skyline 滚动控制 |

## 定位和检查

1. 从当前会话技能目录按精确名称查找实际 `SKILL.md` 路径；不要假定都在同一个根目录。
2. 读取本次需要的技能；其中的相对引用按该技能自身目录解析，不能按本工作流目录解析。
3. 检查所选操作要求的依赖是否齐全。已安装文件不等于其依赖闭包完整，也不等于工具、账号或云环境可用。
4. 必需依赖缺失时，报告具体文件、来源技能、受阻操作，并按源技能要求处理。继续不受影响的工作，不绕过必需协议。

## 已发现的间接依赖

以下是本地检查 `miniprogram-development` 和 `cloud-functions` 时发现的引用，不是本工作流直接调用清单，也不是所有场景都必须安装。是否必需以所选源技能的当前说明和具体操作为准。

| 间接 Skill | 引用来源 | 影响范围 |
|---|---|---|
| `cloudbase-platform` | `miniprogram-development`、`cloud-functions` | 变更安全、部署和敏感数据相关协议；源技能要求时必须先满足 |
| `ui-design` | `miniprogram-development` | 该技能的 UI 生成流程 |
| `auth-tool-cloudbase` | 两者 | 特定 CloudBase 认证配置流程 |
| `cloudbase-wechat-integration` | 两者 | 微信集成相关流程 |
| `ai-model-nodejs` | `cloud-functions` | 服务端 AI 相关流程 |
| `cloudbase-cli` | `cloud-functions` | CLI 相关操作 |
| `cloudrun-development` | `cloud-functions` | CloudRun 相关流程 |
| `http-api-cloudbase` | `cloud-functions` | HTTP API 相关流程 |

2026-09-15 本地检查：16 个直接关联技能可用；上表间接技能的被引用文件存在缺失。该状态是检查时快照，实际执行时重新核实；不是已完成全量递归依赖审计的声明。

`ui-ux-pro-max` 与 `ui-design` 是不同技能，前者已安装不能代替后者满足源技能明确要求。
