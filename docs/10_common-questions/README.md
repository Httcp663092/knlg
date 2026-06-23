# 常见问题库

<!-- NAV_START -->
> **快捷目录**
>
> [首页](../README.md) | [知识地图](../knowledge-map.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](../04_implementation/README.md) | [开发](../05_development-bos/README.md) | [数据](../06_data-model-sql/README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](README.md) | [资料](../90_references/README.md)
>
> 上一章：[问题排查与运维处理手册](../09_operations-issues/issue-triage-and-operations-playbook.md) | 下一章：[全模块高频问题速查](all-module-faq.md) | 本章目录：当前页
<!-- NAV_END -->



这里用于放“日常最容易遇到、最适合快速查”的问题。它和 [运维与问题库](../09_operations-issues/README.md) 的区别是：

| 区域 | 用途 | 记录颗粒度 |
| --- | --- | --- |
| 常见问题库 | 快速判断问题方向，给出排查入口 | 高频问答、短路径、检查清单 |
| 运维与问题库 | 记录一次完整问题处理过程 | 现象、报错、环境、排查、根因、处理、预防 |
| 模块 common-issues | 某个模块的专项问题 | 模块内详细排查逻辑 |

## 当前入口

- [全模块高频问题速查](all-module-faq.md)
- [财务高频问题](finance-faq.md)
- [财务常见问题专项页](../01_finance/common-issues.md)
- [财务案例库](../01_finance/finance-case-library.md)
- [凭证生成与常见分录](../01_finance/voucher-generation-and-entries.md)
- [月结作战手册](../01_finance/month-end-close-playbook.md)

## 问题分类

| 分类 | 适合记录的问题 |
| --- | --- |
| 财务核算 | 凭证、科目、辅助核算、账簿、报表、月结 |
| 往来核销 | 应收、应付、收款、付款、核销、账龄 |
| 资产与折旧 | 资产卡片、变更、处置、折旧、资产对账 |
| 供应链 | 采购、销售、库存、出入库、库存账和财务账 |
| 开发与配置 | BOS、单据字段、插件、工作流、权限、参数 |
| 数据与 SQL | 取数口径、表关系、数据修复、数据对账 |
| 接口与集成 | OpenAPI、外部系统同步、字段映射、失败重试 |
| 环境与发布 | 补丁、部署、缓存、性能、权限、日志 |

## 使用建议

- 不知道问题属于哪个模块时，先看全模块高频问题速查。
- 明确是财务凭证、核销、报表、月结问题时，直接看财务高频问题。
- 已经形成完整排查过程的问题，沉淀到运维与问题库。
- 涉及 SQL 的问题，同步补充到数据模型与 SQL 区。

## 推荐记录格式

短问题可以直接按下面结构补充：

```markdown
## 问题标题

### 现象

### 快速判断

### 排查顺序

### 常见原因

### 处理建议

### 预防
```

如果问题已经影响上线、结账、付款、报表或生产环境，建议再复制 [问题处理模板](../98_templates/issue-resolution.md)，沉淀到 [运维与问题库](../09_operations-issues/README.md)。

## 维护规则

- 一个问题尽量写清“哪个模块、哪个单据、哪个期间、哪个组织、哪个账簿”。
- 报错原文不要只写“报错”，要保留完整提示。
- 财务类问题要优先确认账簿、期间、币别、凭证状态和是否过账。
- 数据类问题要先记录查询口径，再记录 SQL。
- 已经形成稳定处理方法的问题，可以反向补到对应模块正文。
