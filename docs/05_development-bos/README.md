# BOS/插件/二开

<!-- NAV_START -->
> **快捷目录**
>
> [首页](../README.md) | [知识地图](../knowledge-map.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [开发](README.md) | [数据](../06_data-model-sql/README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[金蝶实施交付作战手册](../04_implementation/implementation-delivery-playbook.md) | 下一章：[苍穹开发者工作台与项目创建](cangqiong-developer-portal-project.md) | 本章目录：当前页
<!-- NAV_END -->

这里用于沉淀金蝶 BOS、插件、表单扩展、服务插件、操作插件和二开相关内容。

## 已整理内容

- [苍穹开发者工作台与项目创建](cangqiong-developer-portal-project.md)
- [苍穹单据与基础资料建模](cangqiong-business-object-modeling.md)
- [BOS/苍穹开发实战教程](bos-development-practice-guide.md)

## 推荐内容

- 表单扩展：字段、布局、规则、按钮。
- 单据转换：源单关联、字段映射、数量反写。
- 操作插件：保存、提交、审核、反审核控制。
- 服务插件：后台业务逻辑和批处理。
- 列表插件：批量操作和过滤。
- 动态表单：向导、查询、临时处理界面。
- 权限与菜单：菜单、按钮、数据权限和字段权限。
- 常见开发问题：插件报错、发布失败、权限异常、性能问题。

## 财务相关二开关注点

- 不要破坏凭证生成规则和财务数据一致性。
- 单据字段新增后要关注凭证模板、报表、接口和权限。
- 涉及金额、税额、币别、汇率的逻辑要保留审计线索。
