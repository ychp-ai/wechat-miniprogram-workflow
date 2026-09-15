# cloud · CloudBase 云开发

## 输入与执行

确认项目确实采用 CloudBase、目标环境和本次模块；自建后端任务不迁移到 CloudBase。根据范围读取 auth-wechat-miniprogram、cloud-functions、cloudbase-document-database-in-wechat-miniprogram；按实际需要检查其本地依赖。AI 能力仅在用户要求时读取 ai-model-wechat。

区分客户端数据库访问和服务端云函数 SDK。以受信任的调用身份执行访问控制，明确数据归属、字段校验及权限规则；不把客户端传入用户标识当作授权凭据。密钥不写入小程序包。实现用户指定的数据或函数行为，必要时使用 cloudbase-code-review 检查相关改动。

## 交付与边界

交付代码、数据/权限规则说明和验证证据。开发授权不等于部署授权；用户已授权目标环境部署时继续执行，无需重复确认。否则完成可审阅产物后再处理实际部署授权。缺失环境或工具时明确未部署。
