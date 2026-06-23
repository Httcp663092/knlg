# 金蝶个人知识库

<!-- NAV_START -->
> **快捷目录**
>
> [首页](README.md) | [知识地图](knowledge-map.md) | [财务](01_finance/README.md) | [供应链](02_supply-chain/README.md) | [制造](03_manufacturing/README.md) | [实施](04_implementation/README.md) | [开发](05_development-bos/README.md) | [数据](06_data-model-sql/README.md) | [集成](07_integrations/README.md) | [运维](09_operations-issues/README.md) | [问题](10_common-questions/README.md) | [资料](90_references/README.md)
>
> 上一章：[knlg](../README.md) | 下一章：[金蝶知识地图](knowledge-map.md) | 本章目录：当前页
<!-- NAV_END -->



这里是金蝶知识库的总入口。当前知识库按金蝶项目常见工作域组织：业务模块、实施交付、开发扩展、数据报表、接口集成、环境运维和问题库。

## 核心入口

- [知识地图](knowledge-map.md)：从模块和场景角度查看全库。
- [记录规范](conventions.md)：统一笔记格式、状态、标签和维护规则。
- [财务知识区](01_finance/README.md)：总账、应收、应付、出纳、固定资产、月结和报表。
- [供应链知识区](02_supply-chain/README.md)：采购、销售、库存、存货核算和业财衔接。
- [生产制造知识区](03_manufacturing/README.md)：BOM、计划、生产订单、领料、完工和制造成本。
- [实施方法与交付](04_implementation/README.md)：调研、蓝图、数据迁移、测试、上线和验收。
- [数据模型与 SQL](06_data-model-sql/README.md)：表、字段、取数口径、常用查询。
- [BOS/插件/二开](05_development-bos/README.md)：苍穹开发者工作台、项目创建、单据和基础资料建模。
- [接口与集成](07_integrations/README.md)：AI 文档分类、OpenAPI、外部系统集成。
- [环境、发布和版本](08_environments-releases/README.md)：数据清理、水平分库、环境和补丁。
- [运维与问题库](09_operations-issues/README.md)：问题现象、根因、处理方案。
- [常见问题库](10_common-questions/README.md)：高频问答、快速判断和排查入口。
- [官方资料链接](90_references/official-links.md)：金蝶官方手册、社区和产品资料。
- [模板](98_templates/README.md)：知识笔记、问题处理、实施记录和 SQL 记录模板。

## 推荐使用方式

1. 遇到新问题，先写到 `00_inbox/`、`10_common-questions/` 或 `09_operations-issues/`。
2. 能复用的业务理解，整理到对应模块，例如 `01_finance/`。
3. 涉及表结构、SQL、取数口径，放到 `06_data-model-sql/`。
4. 涉及版本、补丁、环境、部署，放到 `08_environments-releases/`。
5. 重要资料链接和出处，统一补到 `90_references/`。

## 当前覆盖

- 财务：总账、应收、应付、出纳、固定资产、月结、报表、案例和常见问题。
- 供应链：采购、销售、库存、存货核算、业务到财务衔接。
- 生产制造：BOM、MRP、生产订单、委外和制造成本。
- 实施交付：调研蓝图、主数据期初、权限内控、测试培训、上线验收。
- BOS/苍穹开发：项目创建、建模、插件、单据转换、工作流和权限扩展。
- 数据 SQL：数据模型阅读、财务对账、库存排查、报表指标口径。
- 接口集成：外部系统集成、接口联调、日志、幂等、重试和对账。
- 环境运维：环境发布、系统管理员日常、备份恢复、监控巡检、问题处理。

## 笔记状态

- `draft`：草稿，记录未整理完成。
- `active`：正在使用或持续维护。
- `stable`：内容稳定，可作为参考。
- `archived`：已归档，不再主动维护。
