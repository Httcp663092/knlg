# 数据模型与 SQL

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../../index.html) | [文档首页](../README.md) | [知识地图](../knowledge-map.md) | [学习路径](../learning-paths.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](../04_implementation/README.md) | [开发](../05_development-bos/README.md) | [数据](README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[BOS、业务流程与低代码官方资料精读](../05_development-bos/bos-workflow-official-source-digest.md) | 下一章：[数据模型与 SQL 查询作战手册](data-query-playbook.md) | 本章目录：当前页
<!-- NAV_END -->






这里用于沉淀金蝶表结构、字段说明、取数口径和 SQL。重点不是背表名，而是建立“业务单据 -> 数据模型 -> 报表口径 -> 问题证据”的排查能力。

## 目录

- [数据模型与 SQL 查询作战手册](data-query-playbook.md)
- [金蝶数据模型阅读方法](kingdee-data-model-reading-guide.md)
- [财务对账与 SQL 排查教程](finance-reconciliation-sql-guide.md)
- [供应链与库存数据排查教程](supply-chain-inventory-sql-guide.md)
- [报表取数、指标口径与数据分析教程](reporting-metrics-data-analysis-guide.md)
- [财务数据模型](finance/README.md)

## SQL 记录原则

- 写清楚适用产品、版本、账套或数据中心。
- 写清楚查询目的和业务口径。
- 不在生产环境直接执行修改类 SQL。
- 涉及金额、余额、凭证、核销的数据要先备份和复核。
- SQL 结果需要和前台报表交叉验证。

## 推荐学习路径

1. 先读查询作战手册，理解 SQL 排查红线和基本流程。
2. 再读数据模型阅读方法，学会从单据头、分录、状态、关联关系看数据。
3. 做财务问题时读财务对账教程。
4. 做库存、采购、销售、成本问题时读供应链库存教程。
5. 做管理报表、老板驾驶舱、数据分析时读指标口径教程。
