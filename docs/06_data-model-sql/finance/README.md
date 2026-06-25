# 财务数据模型

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../../../index.html) | [文档首页](../../README.md) | [知识地图](../../knowledge-map.md) | [学习路径](../../learning-paths.md) | [财务](../../01_finance/README.md) | [供应链](../../02_supply-chain/README.md) | [制造](../../03_manufacturing/README.md) | [实施](../../04_implementation/README.md) | [开发](../../05_development-bos/README.md) | [数据](../README.md) | [集成](../../07_integrations/README.md) | [运维](../../09_operations-issues/README.md) | [问题](../../10_common-questions/README.md) | [资料](../../90_references/README.md)
>
> 上一章：[报表取数、指标口径与数据分析教程](../reporting-metrics-data-analysis-guide.md) | 下一章：[接口与集成](../../07_integrations/README.md) | 本章目录：当前页
<!-- NAV_END -->






这里作为财务数据和 SQL 的专题索引。财务取数不能只追求“查出来”，更要能说明口径、期间、账簿、组织、币别、凭证状态和业务来源。

## 已整理内容

- [财务对账与 SQL 排查教程](../finance-reconciliation-sql-guide.md)

## 核心对象

- 总账凭证相关表
- 科目和核算维度
- 应收单、收款单和核销关系
- 应付单、付款单和核销关系
- 固定资产卡片和折旧数据
- 现金银行流水和对账数据
- 财务报表取数口径

## 取数时先问清楚

- 查询哪个数据中心或账套。
- 查询哪个账簿、组织和期间。
- 是否包含未审核或未过账数据。
- 是否按原币、本位币或综合本位币统计。
- 是否需要辅助核算维度明细。

## 风险提醒

金蝶数据库表结构可能因产品版本、补丁、二开和客户配置不同而不同。这里的 SQL 必须以实际环境验证后再沉淀。
