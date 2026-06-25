# 实施方法与交付

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../../index.html) | [文档首页](../README.md) | [知识地图](../knowledge-map.md) | [学习路径](../learning-paths.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](README.md) | [开发](../05_development-bos/README.md) | [数据](../06_data-model-sql/README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[制造模块官方资料精读](../03_manufacturing/manufacturing-official-source-digest.md) | 下一章：[金蝶实施交付作战手册](implementation-delivery-playbook.md) | 本章目录：当前页
<!-- NAV_END -->






这里用于沉淀金蝶实施交付方法。目标不是写一套漂亮文档，而是让项目经理、实施顾问、关键用户和运维人员知道每个阶段要做什么、怎么确认、风险在哪里。

## 已整理内容

- [金蝶实施交付作战手册](implementation-delivery-playbook.md)
- [项目调研与蓝图设计详细教程](project-research-and-blueprint-guide.md)
- [主数据与初始化详细教程](master-data-and-initialization-guide.md)
- [权限、角色与内控实施教程](permission-role-control-guide.md)
- [测试、培训与上线演练教程](testing-training-drill-guide.md)
- [上线切换、验收与运维移交教程](go-live-acceptance-handover-guide.md)

## 学习顺序

1. 先读实施交付作战手册，理解项目从启动到验收的全流程。
2. 再读调研与蓝图，把业务现状、未来流程和系统方案定下来。
3. 然后处理主数据、期初和权限，这三类工作决定系统能不能跑起来。
4. 最后按测试、培训、上线、验收顺序推进，确保上线后能持续运行。

## 财务实施重点

- 核算组织和账簿设计。
- 科目表和辅助核算设计。
- 应收应付期初明细。
- 固定资产初始化卡片。
- 月结流程和职责分工。
- 报表公式和管理口径。

## 交付物总清单

| 阶段 | 必备交付物 | 判断标准 |
| --- | --- | --- |
| 启动 | 项目章程、计划、通讯录、风险清单 | 范围、角色、节点、升级机制清楚 |
| 调研 | 调研纪要、现状流程、痛点清单、报表清单 | 业务、财务、仓库、生产关键用户均确认 |
| 蓝图 | 未来流程、配置方案、权限方案、数据方案 | 能用真实案例走通端到端流程 |
| 配置 | 参数清单、基础资料、审批流、凭证模板 | 与蓝图一致，有配置记录 |
| 数据 | 主数据模板、期初模板、导入结果、对账报告 | 导入成功且与旧系统、盘点、总账一致 |
| 测试 | 测试用例、缺陷台账、测试报告 | 关键流程、月结、权限、接口通过 |
| 培训 | 岗位手册、培训签到、练习题、FAQ | 用户能独立完成本岗位操作 |
| 上线 | 切换方案、冻结清单、应急方案、上线报告 | 正式环境可用，首批业务单据可追踪 |
| 验收 | 验收报告、运维移交、归档目录 | 交付物完整，遗留问题有责任人和计划 |
