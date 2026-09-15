# wechat-miniprogram-workflow

一个微信小程序全流程工作流 Skill，包含 11 个子命令。每次只执行选中的能力，不自动推进下一节点。

## 使用

```text
$wechat-miniprogram-workflow <子命令> <目标及要求>
$wechat-miniprogram-workflow help
```

这是 Codex 对话里的调用格式，不是 Shell 命令。

| 子命令 | 能力 | 执行说明 |
|---|---|---|
| `requirements` | 需求梳理 | [requirements.md](references/requirements.md) |
| `design` | UI 设计 | [design.md](references/design.md) |
| `scaffold` | 项目搭建 | [scaffold.md](references/scaffold.md) |
| `feature` | 业务功能 | [feature.md](references/feature.md) |
| `optimize` | 现有功能优化 | [optimize.md](references/optimize.md) |
| `redesign` | 页面重设计 | [redesign.md](references/redesign.md) |
| `cloud` | CloudBase 云开发 | [cloud.md](references/cloud.md) |
| `motion` | 动效交互 | [motion.md](references/motion.md) |
| `polish` | 界面优化 | [polish.md](references/polish.md) |
| `verify` | 测试验收 | [verify.md](references/verify.md) |
| `release` | 预览与发布 | [release.md](references/release.md) |

## 常见场景

```text
$wechat-miniprogram-workflow requirements 梳理门店预约小程序的第一版需求。
$wechat-miniprogram-workflow design 为预约详情页制定布局和视觉规范。
$wechat-miniprogram-workflow feature 实现取消预约功能，复用现有接口。
$wechat-miniprogram-workflow optimize 优化预约提交，解决重复提交和失败重试，保留现有接口，直接实现并验证。
$wechat-miniprogram-workflow optimize 只分析商品列表加载慢的原因，不修改代码。
$wechat-miniprogram-workflow redesign 重新设计并实现首页，突出主要操作，保留现有业务、接口和埋点。
$wechat-miniprogram-workflow redesign 只输出首页的新布局与视觉规范，不修改代码。
$wechat-miniprogram-workflow polish 调整详情页间距、字号和错误提示。
$wechat-miniprogram-workflow verify 只验证预约流程，不修改代码。
$wechat-miniprogram-workflow release 只准备体验版上传材料，不上传。
```

需要组合执行时明确写出：

```text
使用 $wechat-miniprogram-workflow，依次执行 requirements、design，完成后停止。
```

## 安装与结构

将本仓库作为一个 Skill 安装：把包含 `SKILL.md`、`agents/`、`references/` 的整个目录复制或链接到 `${CODEX_HOME:-$HOME/.codex}/skills/wechat-miniprogram-workflow/`。确认新会话发现技能后使用上述命令。

未安装时，可以指定本仓库的 `SKILL.md` 路径，要求按某个子命令执行。仅写入源码仓库不代表已经全局安装。

```text
wechat-miniprogram-workflow/
├── SKILL.md               # 唯一入口、子命令路由、共享约定
├── agents/openai.yaml     # Codex 展示信息
└── references/            # 11 个节点，按子命令加载
```

原 `wx-*` 目录已收敛为参考文档。若在其他位置曾安装旧独立技能，本次仓库整理不会自动删除那些副本。

## 执行范围

现有项目沿用已有框架、渲染器、后端和业务约定。只分析、只设计或直接实现由用户要求决定。CloudBase、Skyline 和其他设计技能按需使用，并核实本地依赖，不假定工具、账号或环境权限已具备。

需求、设计或开发不隐含部署授权；发布子命令按照用户授权的具体动作执行。每次如实交付已完成内容、验证证据和未完成事项。
