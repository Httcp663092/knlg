# 记录规范

<!-- NAV_START -->
> **快捷目录**
>
> [首页](README.md) | [知识地图](knowledge-map.md) | [财务](01_finance/README.md) | [供应链](02_supply-chain/README.md) | [制造](03_manufacturing/README.md) | [实施](04_implementation/README.md) | [开发](05_development-bos/README.md) | [数据](06_data-model-sql/README.md) | [集成](07_integrations/README.md) | [运维](09_operations-issues/README.md) | [问题](10_common-questions/README.md) | [资料](90_references/README.md)
>
> 上一章：[金蝶知识地图](knowledge-map.md) | 下一章：[临时收集箱](00_inbox/README.md) | [本章目录](README.md)
<!-- NAV_END -->




这份规范用于让金蝶个人知识库长期保持可读、可搜索、可复用。

## 文件命名

- 使用小写英文、数字和连字符。
- 文件名表达业务主题，例如 `accounts-receivable.md`、`month-end-close.md`。
- 一个文件尽量只记录一个主要主题。
- 每个目录首页统一使用 `README.md`。
- 不确定归类时先放入 `00_inbox/`。

## 推荐元信息

每篇笔记顶部可以使用以下字段：

```markdown
---
title:
date: 2026-06-22
module:
product: kingdee-cloud-galaxy
tags: []
status: draft
source:
---
```

## 常用标签

- `finance`：财务模块。
- `gl`：总账。
- `ar`：应收。
- `ap`：应付。
- `cashier`：出纳。
- `fixed-assets`：固定资产。
- `implementation`：实施交付。
- `development`：开发或二开。
- `sql`：数据表或取数。
- `issue`：问题排查。
- `reference`：资料链接。

## 写作结构

业务知识建议使用：

```markdown
# 标题

## 适用范围

## 核心概念

## 业务流程

## 关键配置

## 常见问题

## 参考资料
```

问题处理建议使用：

```markdown
# 问题标题

## 现象

## 影响范围

## 排查过程

## 根因

## 解决方案

## 预防措施
```

## 可靠性标记

- `已验证`：在实际环境中操作或核对过。
- `待验证`：来自资料或经验推断，还没在环境中确认。
- `版本相关`：不同金蝶版本或补丁可能表现不同。
- `客户定制`：依赖客户环境、二开或参数配置。

## 整理规则

- 官方资料要保留链接。
- 客户环境差异要写清楚组织、账簿、期间、模块和版本。
- 排查问题时优先记录完整现象和报错原文。
- SQL 笔记必须写清取数目的、过滤条件和风险。
- 移动或归档重要内容后，同步更新 `knowledge-map.md`。
