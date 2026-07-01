# BOS 插件源码级案例：保存校验、操作服务、单据转换与列表过滤

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../../index.html) | [文档首页](../README.md) | [知识地图](../knowledge-map.md) | [学习路径](../learning-paths.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](../04_implementation/README.md) | [开发](README.md) | [数据](../06_data-model-sql/README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[插件治理、排障与上线回归手册](plugin-governance-and-troubleshooting-guide.md) | 下一章：[单据转换、工作流与权限扩展教程](workflow-bill-conversion-permission-guide.md) | [本章目录](README.md)
<!-- NAV_END -->





插件开发、调试与治理页面已经讲了什么时候写插件、如何选事件、怎么做幂等和日志。这篇继续往源码级案例下钻：用保存校验、操作服务、单据转换、列表过滤四类场景，把常见插件写法、风险点和回归测试清单沉淀下来。

注意：下面代码是“结构示意”，不是可直接复制到所有金蝶版本运行的最终代码。具体类名、事件方法、上下文对象、字段标识、取数 API、异常类和注册方式，要以当前产品线、SDK、补丁、客户环境和项目编码规范为准。

## 一、插件案例总览

| 场景 | 推荐插件类型 | 典型业务 | 最大风险 |
| --- | --- | --- | --- |
| 保存校验 | 表单插件或操作服务插件 | 付款申请保存前校验供应商银行资料、预算维度、附件 | 提示不清、性能慢、误拦正常单 |
| 审核后处理 | 操作服务插件 | 审核后生成日志、推送接口、写回状态、生成辅助单据 | 重复执行、事务不一致、反审核困难 |
| 单据转换 | 转换规则或转换插件 | 销售订单下推出库、采购申请下推采购订单时补特殊字段 | 源单关系断裂、数量反写错误 |
| 列表过滤 | 列表插件 | 按当前用户、组织、角色、项目过滤可见数据 | 过滤过宽泄露数据，过滤过窄影响业务 |

## 二、开发前统一模板

每个插件需求先写清楚这张卡片：

```text
需求编号：
插件名称：
业务目标：
标准功能是否可实现：
插件类型：
注册单据：
触发操作：
触发时机：
涉及字段：
涉及分录：
涉及状态：
是否跨组织：
是否影响库存：
是否影响应收应付：
是否影响凭证：
是否调用接口：
幂等键：
日志字段：
异常提示：
回归范围：
回滚方案：
```

如果这张卡片写不出来，不建议直接开始写代码。

## 三、案例 1：保存前校验供应商结算资料

### 业务背景

付款申请保存或提交前，要求供应商必须维护结算银行账号。否则后续银企付款会失败，财务还要退回重做。

### 适用位置

| 选择 | 说明 |
| --- | --- |
| 保存前校验 | 尽早提醒，但草稿阶段可能拦太早 |
| 提交前校验 | 更符合业务正式流转，但保存草稿时不拦 |
| 审核前校验 | 最接近付款责任确认，但问题发现较晚 |

建议：如果草稿也要求完整，就保存前校验；如果允许草稿未完整，放提交前或审核前。

### 伪代码骨架

```java
public class PayApplySupplierBankCheckPlugin /* extends AbstractOperationServicePlugIn */ {

    public void beforeExecuteOperation(OperationContext ctx) {
        for (BillData bill : ctx.getSelectedBills()) {
            String billNo = bill.getBillNo();
            String supplierId = bill.getString("supplier");
            String payOrgId = bill.getString("pay_org");

            if (isBlank(supplierId)) {
                fail(billNo, "供应商为空，无法提交付款申请。");
                continue;
            }

            SupplierBankInfo bankInfo = querySupplierBank(supplierId, payOrgId);
            if (bankInfo == null || isBlank(bankInfo.accountNo)) {
                fail(billNo, "供应商未维护结算银行账号，请先维护供应商结算资料。");
                continue;
            }

            if (!bankInfo.enabled) {
                fail(billNo, "供应商结算银行账号已禁用，请维护有效账号。");
            }
        }
    }

    private SupplierBankInfo querySupplierBank(String supplierId, String payOrgId) {
        // 示例：实际项目按当前环境 API 查询供应商结算资料。
        return null;
    }

    private void fail(String billNo, String message) {
        // 示例：实际项目按框架抛业务校验异常或追加操作错误信息。
    }
}
```

### 检查点

| 检查 | 说明 |
| --- | --- |
| 供应商是否为空 | 不要因为空值导致空指针 |
| 是否按付款组织取结算资料 | 多组织环境下账号可能不同 |
| 是否有默认账号 | 多账号时要明确优先级 |
| 是否启用 | 禁用账号不能继续付款 |
| 提示是否可操作 | 告诉用户去哪维护，而不是抛技术异常 |

### 测试用例

| 用例 | 预期 |
| --- | --- |
| 供应商为空 | 阻止提交，提示供应商为空 |
| 供应商有有效账号 | 通过 |
| 供应商无账号 | 阻止提交 |
| 供应商账号禁用 | 阻止提交 |
| 多组织下 A 组织有账号、B 组织无账号 | A 通过，B 阻止 |

## 四、案例 2：审核后生成接口推送日志

### 业务背景

销售出库单审核后，需要通知外部 WMS、售后系统或数据中台。不能直接盲目推送，因为审核动作可能重试，插件可能重复执行。

### 幂等设计

```text
幂等键 = 业务类型 + 金蝶单据内码 + 单据编号 + 操作类型
```

日志表至少记录：

| 字段 | 用途 |
| --- | --- |
| 幂等键 | 防重复 |
| 单据编号 | 业务追溯 |
| 单据内码 | 精确定位 |
| 业务类型 | 区分销售出库、采购入库等 |
| 推送状态 | 待推送、成功、失败、已补偿 |
| 请求摘要 | 脱敏后的关键字段 |
| 响应摘要 | 外部返回 |
| 重试次数 | 运维处理 |
| 最后错误 | 排查 |

### 伪代码骨架

```java
public class AuditPushLogPlugin /* extends AbstractOperationServicePlugIn */ {

    public void afterExecuteOperation(OperationContext ctx) {
        for (BillData bill : ctx.getSuccessBills()) {
            String idempotentKey = buildKey("SALE_OUT_AUDIT", bill.getId(), bill.getBillNo());

            if (existsPushLog(idempotentKey)) {
                continue;
            }

            PushLog log = new PushLog();
            log.key = idempotentKey;
            log.billId = bill.getId();
            log.billNo = bill.getBillNo();
            log.status = "PENDING";
            log.requestSummary = buildRequestSummary(bill);

            savePushLog(log);
        }
    }

    private String buildKey(String type, String billId, String billNo) {
        return type + ":" + billId + ":" + billNo;
    }

    private boolean existsPushLog(String key) {
        // 示例：查日志表。
        return false;
    }
}
```

### 为什么建议先写日志再异步推送

| 方式 | 风险 |
| --- | --- |
| 审核后同步推接口 | 外部系统慢会卡审核，失败会影响用户体验 |
| 审核后写日志，后台任务推送 | 审核动作快，失败可重试，可补偿 |
| 完全不写日志 | 出问题后无法证明是否推过 |

## 五、案例 3：单据转换时带出项目和预算维度

### 业务背景

采购申请下推采购订单时，要求把项目、预算项目、费用类型从源单带到下游。如果只在表头带，分录可能丢失，后续预算、成本和报表口径会错。

### 优先级

1. 先用标准单据转换字段映射。
2. 标准映射不足时，再用转换插件补充。
3. 不要在下游保存插件里重新猜源单字段。

### 伪代码骨架

```java
public class PurchaseConvertDimensionPlugin /* extends BillConvertPlugin */ {

    public void afterConvert(ConvertContext ctx) {
        for (ConvertRow row : ctx.getRows()) {
            SourceRow source = row.getSourceRow();
            TargetRow target = row.getTargetRow();

            target.set("project", source.get("project"));
            target.set("budget_item", source.get("budget_item"));
            target.set("expense_type", source.get("expense_type"));

            if (isBlank(target.getString("project")) && isProjectRequired(source)) {
                addWarning(row, "源单项目为空，下游采购订单将无法进入项目预算分析。");
            }
        }
    }
}
```

### 检查点

| 检查 | 说明 |
| --- | --- |
| 表头和分录都要看 | 很多维度在分录 |
| 多源单合并下推 | 不同项目不能随意合并 |
| 数量拆分 | 拆分后维度仍要跟随分录 |
| 反写 | 不要破坏源单未下推数量 |
| 预算 | 下游单据是否重复占用预算 |

## 六、案例 4：列表按当前用户过滤项目

### 业务背景

项目型企业希望项目经理只能看到自己负责的项目单据。标准数据权限能做的优先用标准权限；如果需要特殊映射关系，可以用列表过滤补充。

### 伪代码骨架

```java
public class ProjectListFilterPlugin /* extends AbstractListPlugIn */ {

    public void beforeBindData(ListQueryContext ctx) {
        String userId = ctx.getCurrentUserId();

        if (isAdmin(userId)) {
            return;
        }

        List<String> projectIds = queryManagedProjects(userId);
        if (projectIds.isEmpty()) {
            ctx.addFilter("1 = 0");
            return;
        }

        ctx.addInFilter("project", projectIds);
    }

    private List<String> queryManagedProjects(String userId) {
        // 示例：查询用户负责项目关系表。
        return Collections.emptyList();
    }
}
```

### 风险

| 风险 | 控制 |
| --- | --- |
| 管理员也被过滤 | 管理员、审计、财务主管角色要豁免或单独配置 |
| 导出绕过过滤 | 列表过滤和导出权限一起测试 |
| 报表口径不同 | 报表也要同步权限口径 |
| 性能慢 | 项目清单要缓存或控制查询范围 |

## 七、统一日志模板

```text
插件名称：
插件版本：
执行时间：
用户：
组织：
单据类型：
单据编号：
单据内码：
操作：
触发时机：
输入摘要：
输出摘要：
幂等键：
执行状态：
异常信息：
耗时：
```

日志不要记录完整身份证、银行卡、客户敏感地址等隐私字段。需要留痕时保留脱敏摘要。

## 八、回归测试矩阵

| 回归项 | 保存校验 | 审核后日志 | 单据转换 | 列表过滤 |
| --- | --- | --- | --- | --- |
| 新增单据 | 必测 |  |  |  |
| 修改单据 | 必测 |  |  |  |
| 提交审核 | 必测 | 必测 |  |  |
| 反审核 | 视场景 | 必测 |  |  |
| 下推下游 |  |  | 必测 |  |
| 批量操作 | 必测 | 必测 | 必测 |  |
| 多组织 | 必测 | 必测 | 必测 | 必测 |
| 权限用户 | 必测 |  |  | 必测 |
| 接口导入 | 必测 | 必测 |  |  |
| 报表导出 |  |  |  | 必测 |

## 九、上线检查

- 插件需求卡已评审。
- 字段标识和单据标识已按当前环境确认。
- 日志表或日志方案已确认。
- 幂等键已确认。
- 异常提示已由业务确认。
- 测试环境通过正常、异常、批量、多组织用例。
- 回滚方案明确。
- 发布包、版本号、配置变更和代码提交能对应。
- 生产观察指标已配置。

## 十、常见事故和处理

| 事故 | 可能原因 | 处理 |
| --- | --- | --- |
| 保存突然很慢 | 保存插件查大表或调接口 | 移到提交/审核或异步任务，优化查询 |
| 审核生成重复下游 | 没有幂等或重试判断 | 增加幂等键，清理重复单，补对账 |
| 下推后字段丢失 | 转换映射遗漏或分录字段没带 | 补转换规则或转换插件 |
| 用户看不到数据 | 列表过滤过严 | 检查用户项目关系和管理员豁免 |
| 报表和列表不一致 | 列表插件过滤，报表未过滤 | 统一权限口径 |
| 月结后发现插件改金额 | 插件绕过财务控制 | 停用插件，补审计，按流程调整 |

## 十一、和其他专题的关系

- [插件开发、调试与发布教程](plugin-development-debugging-guide.md)：插件基础、类型和开发流程。
- [插件治理、排障与上线回归手册](plugin-governance-and-troubleshooting-guide.md)：插件治理、幂等、事务、日志和生产排障。
- [单据转换、工作流与权限扩展教程](workflow-bill-conversion-permission-guide.md)：单据转换和工作流扩展。
- [权限审计、关键岗位内控与越权操作追溯专题](../04_implementation/permission-audit-sod-control-guide.md)：插件涉及敏感权限和高危动作时要纳入审计。
- [接口联调、监控、重试与对账教程](../07_integrations/interface-debugging-monitoring-reconciliation.md)：审核后推送、补偿和接口日志。

## 十二、维护建议

后续如果拿到实际项目代码，可以把这篇继续升级：

- 按真实基类和事件方法替换伪代码。
- 增加真实字段标识和单据标识。
- 增加真实异常堆栈和处理记录。
- 增加保存插件、操作插件、转换插件、列表插件各一份可编译样例。
