# 数据模型与 SQL

<!-- NAV_START -->
> **快捷目录**
>
> [首页](../README.md) | [知识地图](../knowledge-map.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [开发](../05_development-bos/README.md) | [数据](README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [资料](../90_references/README.md)
>
> 上一章：[苍穹单据与基础资料建模](../05_development-bos/cangqiong-business-object-modeling.md) | 下一章：[财务数据模型](finance/README.md) | 本章目录：当前页
<!-- NAV_END -->

这里用于沉淀金蝶表结构、字段说明、取数口径和 SQL。

## 目录

- [财务数据模型](finance/README.md)

## SQL 记录原则

- 写清楚适用产品、版本、账套或数据中心。
- 写清楚查询目的和业务口径。
- 不在生产环境直接执行修改类 SQL。
- 涉及金额、余额、凭证、核销的数据要先备份和复核。
- SQL 结果需要和前台报表交叉验证。
