# 财务知识区

<!-- NAV_START -->
> **快捷目录**
>
> [首页](../README.md) | [知识地图](../knowledge-map.md) | [财务](README.md) | [供应链](../02_supply-chain/README.md) | [开发](../05_development-bos/README.md) | [数据](../06_data-model-sql/README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [资料](../90_references/README.md)
>
> 上一章：[临时收集箱](../00_inbox/README.md) | 下一章：[财务模块地图](finance-module-map.md) | 本章目录：当前页
<!-- NAV_END -->

这里沉淀金蝶财务模块知识。当前内容以金蝶云·星空公开产品手册和通用实施经验为基础，后续可以根据你的实际环境继续补充截图、菜单路径、参数差异和 SQL。

## 学习顺序

1. [财务模块地图](finance-module-map.md)
2. [财务基础入门：结合金蝶理解](finance-basics-for-kingdee.md)
3. [财务理论到金蝶系统映射](finance-theory-to-kingdee-system.md)
4. [金蝶财务配置指南](kingdee-finance-configuration-guide.md)
5. [财务内控与审计检查清单](finance-control-and-audit-checklist.md)
6. [财务实操场景：从业务单据到凭证报表](finance-operation-scenarios.md)
7. [金蝶财务项目案例集](kingdee-finance-project-cases.md)
8. [财务实务手册](finance-practice-manual.md)
9. [财务实施检查清单](finance-implementation-checklist.md)
10. [财务基础资料与初始化](master-data-and-initialization.md)
11. [总账](general-ledger.md)
12. [凭证生成与常见分录](voucher-generation-and-entries.md)
13. [应收款管理](accounts-receivable.md)
14. [应付款管理](accounts-payable.md)
15. [应收应付对账实务](ar-ap-reconciliation-playbook.md)
16. [出纳与资金](cashier-and-funds.md)
17. [固定资产](fixed-assets.md)
18. [月结流程](month-end-close.md)
19. [月结作战手册](month-end-close-playbook.md)
20. [财务报表与对账](finance-reports.md)
21. [财务案例库](finance-case-library.md)
22. [财务常见问题](common-issues.md)
23. [财务术语](terms.md)

## 财务模块总览

金蝶财务模块通常围绕“业务单据 -> 财务确认 -> 核销/付款/收款 -> 凭证生成 -> 总账过账 -> 报表与月结”展开。

| 模块 | 主要对象 | 关键产出 | 常见角色 |
| --- | --- | --- | --- |
| 总账 | 凭证、账簿、科目、核算维度 | 凭证、账表、结账结果 | 总账会计、主管会计 |
| 应收款 | 应收单、其他应收单、收款单、收款退款单 | 客户往来、收款核销、账龄 | 应收会计 |
| 应付款 | 应付单、其他应付单、付款单、付款退款单 | 供应商往来、付款核销 | 应付会计 |
| 出纳 | 现金、银行、收付款流水 | 银行日记账、资金流水、对账结果 | 出纳 |
| 固定资产 | 资产卡片、变更、处置、折旧 | 折旧凭证、资产台账 | 资产会计 |
| 报表 | 科目余额、明细账、往来账、财务报表 | 资产负债表、利润表、现金流量表 | 财务经理 |

## 优先补充方向

- 本公司实际使用的金蝶产品和版本。
- 财务组织、核算组织、账簿、科目表、会计政策。
- 当前月结顺序和负责人。
- 常见报错、参数差异和客户化功能。
- 财务相关核心表、字段和常用 SQL。

## 本区已经沉淀的实务内容

- 财务上线前调研表、配置清单、验收口径。
- 总账、应收、应付、出纳、固定资产的日常操作主线。
- 凭证模板、凭证生成、凭证生成情况查询和常见分录示例。
- 应收应付和总账的对账方法、差异定位路径。
- 月结从 D-5 到 D+3 的工作安排、检查表和失败排查。
- 财务案例库：把典型报错和差异按“现象、排查、根因、处理”沉淀。
- 财务理论与金蝶系统对象的对应关系：会计要素、科目、账簿、核算维度、凭证和报表。
- 金蝶项目案例：制造企业上线、商贸企业往来治理、月结提速、固定资产上线等。
- 基础财务知识：借贷记账、会计要素、凭证、账簿、三大报表、常见分录。
- 金蝶财务配置：组织、账簿、科目、核算维度、凭证模板、初始化、报表和权限。
- 财务内控：职责分离、手工凭证治理、反审核反结账控制、月结证据包。
