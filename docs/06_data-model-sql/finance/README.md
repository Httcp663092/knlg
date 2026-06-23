# 财务数据模型

<!-- NAV_START -->
> **快捷目录**
>
> [首页](../../README.md) | [知识地图](../../knowledge-map.md) | [财务](../../01_finance/README.md) | [供应链](../../02_supply-chain/README.md) | [开发](../../05_development-bos/README.md) | [数据](../README.md) | [集成](../../07_integrations/README.md) | [运维](../../09_operations-issues/README.md) | [问题](../../10_common-questions/README.md) | [资料](../../90_references/README.md)
>
> 上一章：[数据模型与 SQL](../README.md) | 下一章：[接口与集成](../../07_integrations/README.md) | 本章目录：当前页
<!-- NAV_END -->

这里先作为财务数据和 SQL 的索引，后续可以逐步补充具体表、字段和查询语句。

## 后续补充方向

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
