---
name: wechat-miniprogram-workflow
description: "通过子命令完成微信小程序需求、设计、开发、现有功能优化、页面改版、测试与发布；支持单独执行一个节点或明确指定多个节点。"
---

# 微信小程序全流程工作流

## 调用方式

```text
$wechat-miniprogram-workflow <子命令> <目标及要求>
```

这是对话中的 Skill 路由约定，不是终端 CLI，也不依赖额外命令解析程序。识别用户消息中的子命令后，读取下表中对应的本地参考文件并执行。只加载被选中节点，不一次读取全部参考。`references/` 始终相对于本 `SKILL.md` 所在目录解析（软链接安装同样适用），不能相对于用户项目目录查找。

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

## 路由规则

- `help`：展示子命令表和简短示例，不读取全部节点说明、不修改项目。
- 命令后的自然语言定义目标、范围和交付形式；遵守“只分析”“只设计”“直接实现”“不修改代码”等限定。不要把目标描述里的其他命令单词当作第二个节点。
- 未给子命令但意图明确时选择一个匹配节点并简述选择。缺少目标且无法从项目上下文推断时，只问关键缺项；不要启动全流程。
- 无法识别的显式命令只提示支持的命令，不猜测执行。没有 `all` 默认全流程行为。
- 用户明确要求多个节点（例如“依次执行 requirements、design”）才依序执行；把前一个交付物作为后一个输入，完成指定序列后停止。
- 旧名 `wx-requirements`、`wx-ui-design`、`wx-scaffold`、`wx-feature`、`wx-feature-optimize`、`wx-page-redesign`、`wx-cloud`、`wx-motion`、`wx-ui-polish`、`wx-verify`、`wx-release` 在本 Skill 已加载的对话中分别对应上述节点；它们不再是本包独立 Skill 的名称。

## 易混淆的选择

- `feature`：实现新增或明确要求的功能；`optimize`：诊断并改进现有功能。优化要求默认包含实现，明确只分析时仅输出方案。
- `design`：设计页面及规范；`polish`：局部视觉/文案打磨；`redesign`：现有页面结构和视觉的整体改版。
- `redesign` 配合“只出设计”只交付方案；“重新设计并实现”完成代码落地。“重做页面设计”按设计范围交付，不自行扩大为业务改造。
- `verify` 的检查不能替代 `release` 的实际平台操作。`release` 必须区分准备、预览、上传、提审与正式发布；子命令本身不授予所有动作权限。

## 共享执行约定


- 只完成用户指定的本节点范围；不自动串联其他节点。用户明确指定多个节点时才按其顺序执行。
- 优先读取项目现状、现有文档和用户输入；不要求先运行前置节点。不足以影响决策的信息采用注明的合理假设，只有真正阻塞的内容才询问。
- 目标项目优先使用用户指定路径，其次使用当前工作项目；技能安装目录只存放指令，不作为业务项目写入。没有可识别的目标项目时，设计和需求可使用已有描述继续，代码修改必须先确定目标目录。
- 沿用项目框架、渲染器、后端和目录约定，不默认切换为原生、Skyline 或 CloudBase。只在当前节点确实需要技术选择时确认关键选项；需求分析和纯设计不以 AppID、云环境或框架选型为前置条件。
- 默认交付物写入目标项目已有约定位置；无约定时文档放 docs/miniprogram/。用户明确“只回复/不写文件/只读”时直接在对话交付，不创建报告文件；“不修改代码”仍可按请求输出文档。只更新本次范围，不覆盖已有结论。多个页面的报告采用页面名称或独立小节，避免相互覆盖。
- 结束时说明产物位置、实际验证结果、未完成项。建议后续节点可以，但不自行执行。
- 以下关联技能是按需增强项，不是必经工作流。使用时从当前可用技能目录定位并读取；遵守其真实依赖要求，不绕过缺失协议。若关联技能未安装，先按本节点自包含说明完成可独立执行的工作。若已读取的技能要求缺失依赖，说明缺项及所阻塞的具体操作，按其要求补齐后才能继续该操作；可继续无关的需求、设计和只读检查，不将同一操作改名后绕过协议，不声称已执行该技能。不要远程抓取技能正文代替安装。


## 示例

```text
$wechat-miniprogram-workflow optimize 优化预约提交，保留接口，解决重复提交并验证。
$wechat-miniprogram-workflow redesign 重新设计并实现预约详情页，保留业务功能。
$wechat-miniprogram-workflow redesign 只输出首页的新布局和视觉规范，不修改代码。
$wechat-miniprogram-workflow verify 只验证取消预约流程，不修改代码。
$wechat-miniprogram-workflow release 只做体验版上传准备，不上传。
```
