# 真实环境已验证 SQL 示例库

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../../index.html) | [文档首页](../README.md) | [知识地图](../knowledge-map.md) | [学习路径](../learning-paths.md) | [财务](../01_finance/README.md) | [供应链](../02_supply-chain/README.md) | [制造](../03_manufacturing/README.md) | [实施](../04_implementation/README.md) | [开发](../05_development-bos/README.md) | [数据](README.md) | [集成](../07_integrations/README.md) | [运维](../09_operations-issues/README.md) | [问题](../10_common-questions/README.md) | [资料](../90_references/README.md)
>
> 上一章：[核心表字典与常用 SQL 查询包](core-table-dictionary-and-sql-pack.md) | 下一章：[财务对账与 SQL 排查教程](finance-reconciliation-sql-guide.md) | [本章目录](README.md)
<!-- NAV_END -->




这篇用于沉淀“真实环境已经跑过、能回前台验证、可复用”的 SQL。它和 [核心表字典与常用 SQL 查询包](core-table-dictionary-and-sql-pack.md) 的区别是：查询包提供结构模板，本页要求每条 SQL 都带业务场景、参数口径、前台验证入口、样例结果和风险说明。

注意：下面的 SQL 使用“中文对象名/字段名”作为结构化占位，不代表某个版本的物理表名。落地到金蝶云·星空、苍穹或客户二开环境时，必须用当前环境的元数据、数据库字典、开发平台或已验证 SQL 替换表名字段。

## 一、验证等级

| 等级 | 含义 | 可用于 |
| --- | --- | --- |
| template | 只有查询结构，还没有替换当前环境表名字段 | 学习、设计、评审 |
| env-ready | 已按某个测试环境替换表名字段，但没有前台抽样截图 | 测试环境排查 |
| verified | 已在指定环境执行，并用前台单据、标准报表或导出结果核对 | 同环境同版本复用 |
| deprecated | 表结构、版本或业务口径变化，不建议继续使用 | 历史参考 |

每条 SQL 进入本页时，默认先标 `template`。只有补齐“环境、表字段来源、样例单号、前台验证入口、验证日期、验证人、结果截图或导出文件”后，才能改成 `verified`。

## 二、SQL 记录卡

````markdown
## 示例名称

- 状态：template / env-ready / verified / deprecated
- 适用环境：
- 数据库类型：SQL Server / Oracle / PostgreSQL / 其他
- 适用模块：
- 业务场景：
- 前台验证入口：
- 样例单号或报表条件：
- 表字段来源：
- 验证日期：
- 风险等级：低 / 中 / 高

### 业务口径

- 组织：
- 期间：
- 日期：
- 状态：
- 金额：
- 数量：
- 币别：

### SQL

```sql
-- 只读查询。生产环境禁止直接 update/delete/insert。
```

### 样例结果

| 字段 | 样例 | 说明 |
| --- | --- | --- |

### 前台验证

- 菜单：
- 单据：
- 报表：
- 结论：

### 风险和限制

- 待补充。
````

## 三、通用参数约定

```sql
-- :org_id       组织内码
-- :book_id      账簿内码
-- :period       期间，例如 2026-06
-- :date_from    开始日期，含当天
-- :date_to      结束日期，不含当天
-- :bill_no      单据编号
-- :material_id  物料内码
-- :customer_id  客户内码
-- :supplier_id  供应商内码
-- :external_no  外部业务号
-- :amount_tol   金额容差
-- :qty_tol      数量容差
```

不同数据库变量写法不同。SQL Server 可以用变量或参数，Oracle 常用绑定变量，PostgreSQL 常用 `$1` 或应用侧参数。不要把参数写死在生产排查 SQL 里。

## 四、单据状态与分录核对

### 1. 按单据编号查头表、状态和操作人

- 状态：template
- 适用模块：全模块
- 业务场景：用户给出单号后，先判断单据是否存在、组织是否正确、是否审核、是否关闭。
- 前台验证入口：对应单据列表或单据详情。

```sql
select
  h.单据内码,
  h.单据编号,
  h.单据日期,
  h.业务组织,
  h.单据类型,
  h.单据状态,
  h.审核状态,
  h.关闭状态,
  h.创建人,
  h.创建时间,
  h.审核人,
  h.审核时间
from 单据头表 h
where h.单据编号 = :bill_no;
```

验证要点：

- 前台能否打开同一张单据。
- 单据日期是否落在用户报表查询期间。
- 组织、单据类型、状态是否和用户描述一致。
- 如果查不到，先确认编号是否来自外部系统、打印单号、源单号或历史归档。

### 2. 按单据编号查分录、物料、数量和金额

- 状态：template
- 适用模块：采购、销售、库存、生产、财务
- 业务场景：用户只看头表金额，但差异常在分录、批号、仓库、税额或单位。
- 前台验证入口：单据详情的明细页签。

```sql
select
  h.单据编号,
  e.分录行号,
  e.物料编码,
  e.物料名称,
  e.仓库,
  e.批号,
  e.业务数量,
  e.基本数量,
  e.含税单价,
  e.不含税金额,
  e.税额,
  e.价税合计,
  e.分录状态
from 单据头表 h
join 单据分录表 e
  on e.单据内码 = h.单据内码
where h.单据编号 = :bill_no
order by e.分录行号;
```

常见发现：

- 前台汇总金额和分录金额因为折扣、税额尾差或币别不同而不一致。
- 用户按业务单位看数量，后台按基本单位或库存单位显示。
- 批号、库位、库存状态没有在报表条件里过滤一致。

## 五、凭证生成和总账追溯

### 3. 查业务单据是否生成凭证

- 状态：template
- 适用模块：应收、应付、存货核算、固定资产、费用报销
- 业务场景：业务单据已审核，但总账没有金额或凭证生成失败。
- 前台验证入口：智能会计平台、凭证生成情况查询、总账凭证。

```sql
select
  b.单据编号,
  b.单据日期,
  b.业务组织,
  b.业务金额,
  g.生成状态,
  g.生成日志,
  v.凭证号,
  v.凭证日期,
  v.账簿,
  v.会计期间,
  v.凭证状态,
  v.过账状态
from 业务单据头表 b
left join 凭证生成记录表 g
  on g.源单内码 = b.单据内码
left join 凭证头表 v
  on v.凭证内码 = g.凭证内码
where b.单据编号 = :bill_no;
```

判断：

- 没有生成记录：看凭证模板、生成条件、单据状态、期间。
- 有生成记录但失败：保存完整错误信息和模板编码。
- 有凭证未过账：总账余额和报表可能不会体现。
- 账簿不一致：检查组织到账簿映射和凭证生成方案。

### 4. 查凭证分录科目和辅助核算

- 状态：template
- 适用模块：财务、业财对账
- 业务场景：凭证生成了，但科目、部门、客户、供应商、项目或金额不对。
- 前台验证入口：总账凭证详情。

```sql
select
  v.凭证号,
  v.凭证日期,
  v.账簿,
  d.分录行号,
  d.摘要,
  d.科目编码,
  d.科目名称,
  d.借方本位币金额,
  d.贷方本位币金额,
  d.客户,
  d.供应商,
  d.部门,
  d.项目,
  d.物料
from 凭证头表 v
join 凭证分录表 d
  on d.凭证内码 = v.凭证内码
where v.凭证号 = :voucher_no
  and v.账簿 = :book_id
order by d.分录行号;
```

排查时不要只看科目。很多“金额对但报表不对”的问题，是辅助核算维度没有带出来，导致辅助明细账或管理报表取不到。

## 六、应收应付和核销

### 5. 查客户未核销应收明细

- 状态：template
- 适用模块：应收、销售、资金
- 业务场景：客户说余额不对、账龄不对、收款已经收到但应收仍未清。
- 前台验证入口：应收明细表、客户余额表、应收账龄分析表。

```sql
select
  ar.客户,
  ar.单据编号,
  ar.业务日期,
  ar.到期日,
  ar.币别,
  ar.应收金额,
  ar.已核销金额,
  ar.未核销金额,
  ar.账龄天数,
  ar.单据状态,
  ar.凭证号
from 应收明细表 ar
where ar.客户 = :customer_id
  and ar.业务日期 < :date_to
  and abs(ar.未核销金额) > :amount_tol
order by ar.到期日, ar.单据编号;
```

验证要点：

- 是否按结算客户还是收货客户查询。
- 是否包含未审核应收单。
- 是否包含未过账凭证。
- 是否按业务日期、到期日还是会计期间统计账龄。

### 6. 查付款或收款核销关系

- 状态：template
- 适用模块：应收、应付、资金
- 业务场景：用户反馈“钱付了/收了，但往来余额没变”。
- 前台验证入口：收款单、付款单、核销记录、客户/供应商明细。

```sql
select
  m.核销单号,
  m.核销日期,
  m.往来对象,
  s.源单编号 as 应收应付单号,
  s.源单金额,
  p.收付款单号,
  p.收付款金额,
  m.本次核销金额,
  m.核销状态
from 核销主表 m
join 核销源单明细 s
  on s.核销内码 = m.核销内码
join 核销收付款明细 p
  on p.核销内码 = m.核销内码
where m.往来对象 = :customer_or_supplier_id
  and m.核销日期 >= :date_from
  and m.核销日期 < :date_to
order by m.核销日期, m.核销单号;
```

常见原因：

- 收款单已保存但未审核。
- 收款单已审核但未核销。
- 核销对象选错，例如客户和结算客户不一致。
- 凭证未生成或未过账，业务余额和总账余额不同。

## 七、库存、批号和成本

### 7. 查物料即时库存分布

- 状态：template
- 适用模块：库存、供应链、制造
- 业务场景：用户说库存不对，先按仓库、库位、批号、库存状态拆开。
- 前台验证入口：即时库存、库存明细账、物料收发明细。

```sql
select
  inv.库存组织,
  inv.物料编码,
  inv.物料名称,
  inv.仓库,
  inv.库位,
  inv.批号,
  inv.库存状态,
  sum(inv.库存数量) as 库存数量,
  sum(inv.可用数量) as 可用数量,
  sum(inv.锁定数量) as 锁定数量
from 即时库存表 inv
where inv.库存组织 = :org_id
  and inv.物料内码 = :material_id
group by inv.库存组织, inv.物料编码, inv.物料名称, inv.仓库, inv.库位, inv.批号, inv.库存状态
order by inv.仓库, inv.库位, inv.批号, inv.库存状态;
```

判断：

- 有库存不代表可用，可能在待检、冻结、锁定或不良状态。
- 批号和库位不一致时，前台只查仓库会误判。
- WMS 或条码系统回传延迟时，要再查出入库单状态。

### 8. 查负库存或零成本候选

- 状态：template
- 适用模块：库存、存货核算、制造成本
- 业务场景：月结前查负库存、0 成本、异常成本，避免出库成本和凭证异常。
- 前台验证入口：库存明细账、出库成本核算、存货收发存汇总表。

```sql
select
  c.核算组织,
  c.期间,
  c.物料编码,
  c.物料名称,
  c.仓库,
  c.批号,
  sum(c.结存数量) as 结存数量,
  sum(c.结存金额) as 结存金额,
  case
    when sum(c.结存数量) < 0 then '负库存'
    when sum(c.结存数量) <> 0 and abs(sum(c.结存金额)) <= :amount_tol then '有数量无金额'
    when sum(c.结存数量) = 0 and abs(sum(c.结存金额)) > :amount_tol then '无数量有金额'
    else '待复核'
  end as 异常类型
from 存货核算余额表 c
where c.核算组织 = :org_id
  and c.期间 = :period
group by c.核算组织, c.期间, c.物料编码, c.物料名称, c.仓库, c.批号
having sum(c.结存数量) < 0
    or (sum(c.结存数量) <> 0 and abs(sum(c.结存金额)) <= :amount_tol)
    or (sum(c.结存数量) = 0 and abs(sum(c.结存金额)) > :amount_tol)
order by 异常类型, c.物料编码, c.仓库;
```

这类 SQL 只负责找候选。最终处理要回到前台看入库成本、出库核算、成本调整、暂估、负库存和期初余额。

## 八、采购结算和暂估

### 9. 查采购入库未到票或暂估未冲回

- 状态：template
- 适用模块：采购、应付、存货核算
- 业务场景：采购入库已发生，但发票未到或暂估未冲回，导致应付和成本差异。
- 前台验证入口：采购入库单、采购发票、应付单、暂估应付、采购结算。

```sql
select
  r.供应商,
  r.入库单号,
  r.入库日期,
  r.物料编码,
  r.入库数量,
  r.入库金额,
  i.发票号,
  i.到票数量,
  i.到票金额,
  s.暂估金额,
  s.冲回金额,
  r.入库金额 - coalesce(i.到票金额, 0) as 到票差额
from 采购入库明细 r
left join 采购发票匹配明细 i
  on i.入库分录内码 = r.分录内码
left join 暂估应付明细 s
  on s.入库分录内码 = r.分录内码
where r.入库日期 >= :date_from
  and r.入库日期 < :date_to
  and r.库存组织 = :org_id
  and (i.发票号 is null or abs(r.入库金额 - coalesce(i.到票金额, 0)) > :amount_tol)
order by r.供应商, r.入库日期, r.入库单号;
```

判断：

- 未到票不一定错误，可能是正常暂估。
- 到票金额和入库金额差异要区分价差、费用分摊和税额差异。
- 跨月到票时要看暂估冲回期间。

## 九、销售、收入和毛利

### 10. 销售出库、应收、收入确认和成本勾稽

- 状态：template
- 适用模块：销售、应收、收入、存货核算
- 业务场景：销售已发货，但收入、应收、成本、毛利口径不一致。
- 前台验证入口：销售出库单、应收单、收入确认、销售毛利分析、总账凭证。

```sql
select
  so.销售组织,
  so.客户,
  so.销售出库单号,
  so.出库日期,
  so.物料编码,
  so.出库数量,
  ar.应收单号,
  ar.应收金额,
  rev.收入确认单号,
  rev.确认收入金额,
  cost.出库成本,
  rev.确认收入金额 - cost.出库成本 as 毛利
from 销售出库明细 so
left join 应收来源明细 ar
  on ar.源单分录内码 = so.分录内码
left join 收入确认明细 rev
  on rev.源单分录内码 = so.分录内码
left join 出库成本明细 cost
  on cost.出库分录内码 = so.分录内码
where so.出库日期 >= :date_from
  and so.出库日期 < :date_to
  and so.销售组织 = :org_id
order by so.客户, so.出库日期, so.销售出库单号;
```

验证要点：

- 是否按出库、签收、开票、应收还是收入确认日期取数。
- 是否包含退货、红字应收、红字发票。
- 成本是否已经核算并生成凭证。

## 十、生产和 MES 回写

### 11. 查生产订单、报工、完工入库差异

- 状态：template
- 适用模块：制造、MES 集成、存货核算
- 业务场景：MES 显示已完成，但金蝶生产订单、报工单或完工入库数量不一致。
- 前台验证入口：生产订单、报工单、完工入库单、MES 日报工对账表。

```sql
select
  mo.生产订单号,
  mo.物料编码,
  mo.计划数量,
  sum(r.报工合格数量) as 报工合格数量,
  sum(r.报工不良数量) as 报工不良数量,
  sum(inb.完工入库数量) as 完工入库数量,
  sum(r.报工合格数量) - sum(inb.完工入库数量) as 报工入库差异,
  max(r.最后报工时间) as 最后报工时间,
  max(inb.最后入库时间) as 最后入库时间
from 生产订单表 mo
left join 报工汇总表 r
  on r.生产订单内码 = mo.生产订单内码
left join 完工入库汇总表 inb
  on inb.生产订单内码 = mo.生产订单内码
where mo.生产订单号 = :bill_no
group by mo.生产订单号, mo.物料编码, mo.计划数量;
```

判断：

- 报工合格数大于入库数：可能最后工序未入库、质检未放行、入库单未审核。
- 入库数大于报工数：可能手工入库、回写重复或不启用工序报工。
- MES 已报工但 SQL 查不到：先查接口日志和外部报工流水。

### 12. 按 MES 外部报工流水查回写结果

- 状态：template
- 适用模块：MES 集成、接口、制造
- 业务场景：定位某条 MES 报工到底有没有进入金蝶。
- 前台验证入口：接口日志、MES 报工日志、金蝶报工单。

```sql
select
  l.接口名称,
  l.外部报工流水号,
  l.外部工单号,
  l.金蝶生产订单号,
  l.金蝶报工单号,
  l.请求时间,
  l.响应状态,
  l.错误信息,
  l.重试次数,
  r.报工单状态,
  r.审核状态
from MES接口日志表 l
left join 报工单表 r
  on r.报工单号 = l.金蝶报工单号
where l.外部报工流水号 = :external_no
order by l.请求时间;
```

这条结果要和 [车间看板、MES 报工回写与设备数据采集专题](../03_manufacturing/mes-shop-floor-dashboard-data-collection-guide.md) 里的回写日志、幂等键和异常处理一起看。

## 十一、接口日志和重复单

### 13. 按外部业务号查推单链路

- 状态：template
- 适用模块：接口、WMS、MES、OA、CRM、电商
- 业务场景：外部系统说已推送，金蝶说没收到或重复生成。
- 前台验证入口：接口日志、业务单据列表、外部系统日志。

```sql
select
  l.接口名称,
  l.外部业务号,
  l.幂等键,
  l.金蝶单据类型,
  l.金蝶单据编号,
  l.请求时间,
  l.响应时间,
  l.响应状态,
  l.错误信息,
  l.重试次数
from 接口日志表 l
where l.外部业务号 = :external_no
order by l.请求时间;
```

判断：

- 同一幂等键多次成功：幂等控制失效。
- 第一次成功、后续失败：外部系统可能没收到成功响应。
- 只有失败没有单据：查主数据、状态、权限、必填字段。

### 14. 查某期间外部业务号重复候选

- 状态：template
- 适用模块：接口、数据治理
- 业务场景：批量扫描重复推单风险。
- 前台验证入口：业务单据列表、接口监控、外部系统台账。

```sql
select
  l.接口名称,
  l.外部业务号,
  count(distinct l.金蝶单据编号) as 金蝶单据数,
  min(l.请求时间) as 首次请求时间,
  max(l.请求时间) as 最后请求时间,
  max(l.错误信息) as 最近错误信息
from 接口日志表 l
where l.请求时间 >= :date_from
  and l.请求时间 < :date_to
  and l.响应状态 = '成功'
group by l.接口名称, l.外部业务号
having count(distinct l.金蝶单据编号) > 1
order by 金蝶单据数 desc, 最后请求时间 desc;
```

注意：一张外部订单允许分批入库或分批出库时，不能只凭多张金蝶单据判断重复，必须看业务类型、分录、数量和源单关系。

## 十二、主数据和组织范围

### 15. 查物料、客户、供应商是否禁用或组织不可用

- 状态：template
- 适用模块：全模块、接口、权限
- 业务场景：前台保存失败、接口提示基础资料不存在、下推时引用异常。
- 前台验证入口：基础资料列表、使用组织、控制策略。

```sql
select
  m.基础资料类型,
  m.编码,
  m.名称,
  m.状态,
  m.创建组织,
  u.使用组织,
  u.分配状态,
  u.是否可用
from 基础资料主表 m
left join 基础资料组织使用表 u
  on u.基础资料内码 = m.基础资料内码
where m.编码 in (:master_codes)
order by m.基础资料类型, m.编码, u.使用组织;
```

常见原因：

- 基础资料在创建组织可见，但业务组织未分配。
- 编码相同但数据中心不同。
- 外部系统传的是旧编码、客户料号或供应商料号。
- 基础资料已禁用但历史单据仍引用。

## 十三、月结前异常清单

### 16. 一次性输出月结前待处理数量

- 状态：template
- 适用模块：财务、供应链、制造、运维
- 业务场景：月结前快速看阻塞项，不替代详细排查。
- 前台验证入口：未审核单据列表、凭证生成情况、库存关账、成本计算、接口监控。

```sql
select '未审核业务单据' as 检查项, count(*) as 数量
from 单据头表
where 业务日期 >= :date_from
  and 业务日期 < :date_to
  and 业务组织 = :org_id
  and 审核状态 <> '已审核'
union all
select '已审核未生成凭证' as 检查项, count(*) as 数量
from 业务单据头表 b
left join 凭证生成记录表 g
  on g.源单内码 = b.单据内码
where b.业务日期 >= :date_from
  and b.业务日期 < :date_to
  and b.业务组织 = :org_id
  and b.审核状态 = '已审核'
  and g.凭证内码 is null
union all
select '接口失败未处理' as 检查项, count(*) as 数量
from 接口日志表 l
where l.请求时间 >= :date_from
  and l.请求时间 < :date_to
  and l.响应状态 = '失败'
  and l.处理状态 <> '已处理'
union all
select '负库存候选' as 检查项, count(*) as 数量
from 即时库存表 inv
where inv.库存组织 = :org_id
  and inv.库存数量 < 0;
```

这类汇总适合做日报或月结晨会，不适合直接作为修复依据。每个检查项都要能下钻到明细 SQL。

## 十四、从模板走向 verified 的步骤

1. 从前台拿到真实单号、报表条件或接口外部业务号。
2. 在测试环境用当前表名字段替换模板。
3. 限定组织、期间、状态和样例范围。
4. 执行只读 SQL，保存结果。
5. 回前台单据或标准报表逐项核对。
6. 记录差异原因、截图、导出文件和验证日期。
7. 把状态从 `template` 改成 `env-ready` 或 `verified`。
8. 如果用于生产月结或财务报表，至少再由业务顾问或财务复核一次。

## 十五、关联阅读

- [数据模型与 SQL 查询作战手册](data-query-playbook.md)
- [金蝶数据模型阅读方法](kingdee-data-model-reading-guide.md)
- [核心表字典与常用 SQL 查询包](core-table-dictionary-and-sql-pack.md)
- [财务对账与 SQL 排查教程](finance-reconciliation-sql-guide.md)
- [供应链与库存数据排查教程](supply-chain-inventory-sql-guide.md)
- [报表取数、指标口径与数据分析教程](reporting-metrics-data-analysis-guide.md)
- [真实环境内容收集与沉淀清单](../00_inbox/real-environment-content-intake.md)
