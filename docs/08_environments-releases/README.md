# 环境、发布和版本

<!-- NAV_START -->
> **快捷目录**
>
> [首页](../README.md) | [知识地图](../knowledge-map.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](../04_implementation/README.md) | [开发](../05_development-bos/README.md) | [数据](../06_data-model-sql/README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[AI 文档分类与结构化提取](../07_integrations/ai-document-classification.md) | 下一章：[环境、版本与发布运维手册](environment-release-ops-guide.md) | 本章目录：当前页
<!-- NAV_END -->




这里用于沉淀金蝶环境、版本、补丁、发布和部署记录。

## 已整理内容

- [环境、版本与发布运维手册](environment-release-ops-guide.md)
- [系统管理员日常运维教程](system-admin-daily-ops-guide.md)
- [备份、恢复、监控与性能巡检教程](backup-restore-monitoring-guide.md)
- [苍穹数据清理服务](cangqiong-data-cleaning.md)
- [苍穹水平分库](cangqiong-horizontal-sharding.md)

## 维护重点

- 环境清单：DEV、TEST、UAT、PROD、DR。
- 产品版本和补丁记录。
- 发布步骤和回滚方案。
- 权限、账号、接口账号。
- 数据中心、备份和恢复。
- 日志、监控、告警和性能。
- 数据清理、归档、水平分库等容量治理能力。

## 财务相关关注点

- 月结期间避免随意发布影响财务单据、凭证和报表的变更。
- 版本升级前要验证财务凭证生成、报表公式、核销和月结。
- 重要补丁要记录影响范围和回归测试结果。
