# 接口与集成

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../../index.html) | [文档首页](../README.md) | [知识地图](../knowledge-map.md) | [学习路径](../learning-paths.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](../04_implementation/README.md) | [开发](../05_development-bos/README.md) | [数据](../06_data-model-sql/README.md) | [集成](README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[财务数据模型](../06_data-model-sql/finance/README.md) | 下一章：[金蝶接口集成实施教程](integration-implementation-guide.md) | 本章目录：当前页
<!-- NAV_END -->






这里用于沉淀金蝶与外部系统集成的资料。

## 已整理内容

- [金蝶接口集成实施教程](integration-implementation-guide.md)
- [外部系统集成场景教程](external-system-integration-scenarios.md)
- [接口联调、监控、重试与对账教程](interface-debugging-monitoring-reconciliation.md)
- [WebAPI、集成平台与安全参数官方资料精读](webapi-integration-official-source-digest.md)
- [AI 文档分类与结构化提取](ai-document-classification.md)

## 覆盖范围

- Web API / OpenAPI。
- 第三方系统对接：电商、WMS、MES、OA、CRM。
- 银企直连。
- 税务和发票平台。
- 电子会计档案。
- 数据同步和中间库。
- 接口日志、幂等、重试、对账和监控。
- 接口上线后的日常巡检、失败补偿和财务对账。

## 财务集成关注点

- 外部单据进入金蝶后是否形成正式财务单据。
- 金额、税额、币别、汇率和核算维度是否完整。
- 接口失败是否有重试、幂等和异常处理。
- 财务凭证生成是否可追溯到外部来源。
