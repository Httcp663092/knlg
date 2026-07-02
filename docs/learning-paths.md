# 金蝶知识库学习路径

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../index.html) | [文档首页](README.md) | [知识地图](knowledge-map.md) | [学习路径](learning-paths.md) | [财务](01_finance/README.md) | [供应链](02_supply-chain/README.md) | [制造](03_manufacturing/README.md) | [实施](04_implementation/README.md) | [开发](05_development-bos/README.md) | [数据](06_data-model-sql/README.md) | [集成](07_integrations/README.md) | [运维](09_operations-issues/README.md) | [问题](10_common-questions/README.md) | [资料](90_references/README.md)
>
> 上一章：[金蝶知识地图](knowledge-map.md) | 下一章：[知识库缺口与补充路线图](knowledge-gap-roadmap.md) | [本章目录](README.md)
<!-- NAV_END -->


这页不是目录的重复，而是把知识库拆成几条可以执行的学习路线。每条路线都包含“先学什么、做什么练习、交付什么成果、怎么判断学会了”，适合自己学习，也适合带新人、带关键用户或做项目交接。

## 使用方法

1. 先按自己的角色选择路线，不要一上来从第一篇文档顺序读到最后。
2. 每读完一组文档，就在测试环境做一次真实单据或真实配置。
3. 每个阶段至少留下一个成果物，例如配置清单、测试用例、问题记录、对账表或操作手册。
4. 遇到问题先进入 [常见问题库](10_common-questions/README.md)，形成完整处理过程后沉淀到 [运维与问题库](09_operations-issues/README.md)。

## 路线一：财务新人到金蝶财务主办

适合对象：总账会计、应收会计、应付会计、出纳、财务主管、刚接触金蝶财务模块的人。

目标：能够理解财务业务在金蝶系统里的落地方式，独立完成日常凭证、往来、资金、月结、报表和基础排查。

配套课件：

- [金蝶云星瀚总账培训 PPT](resources/training/金蝶云星瀚总账培训.pptx)：适合作为财务新人、总账会计和实施顾问的 30-60 分钟总账入门培训。

### 第一阶段：把财务语言翻译成系统语言

先读：

- [财务模块地图](01_finance/finance-module-map.md)
- [财务基础入门：结合金蝶理解](01_finance/finance-basics-for-kingdee.md)
- [财务基础通俗入门：从业务、凭证到报表](01_finance/finance-starter-plain-language-guide.md)
- [会计循环与金蝶系统落地教程](01_finance/accounting-cycle-kingdee-guide.md)
- [财务理论到金蝶系统映射](01_finance/finance-theory-to-kingdee-system.md)

要弄懂的关键问题：

- 为什么业务单据不是财务凭证，但可以成为凭证来源。
- 为什么科目、核算维度、组织、账簿、期间、币别必须一起看。
- 为什么应收、应付、出纳、固定资产、存货核算最终都要和总账对上。
- 为什么金蝶里“审核、过账、结账、反结账”是财务控制动作，不只是按钮。
- 为什么采购、销售、库存这些业务单据会影响资产、负债、收入、成本、费用和报表。

实操练习：

1. 在测试环境建立一个最小业务链路：采购入库、应付确认、付款、凭证、总账查询。
2. 建立一个销售链路：销售出库、应收确认、收款、核销、凭证、客户明细账。
3. 用一个采购和一个销售例子说明资产、负债、收入、成本、费用分别怎么变化。
4. 查询一张凭证，反查来源单据、业务对象、核算维度和附件。

验收标准：

- 能说明一张凭证从哪个业务动作来，为什么借贷方向是这样。
- 能说清“业务已发生但凭证没有生成”和“凭证已生成但没有过账”的差别。
- 能用科目余额表、明细账、辅助核算明细账说明一笔余额。

### 第二阶段：掌握财务配置和主数据

先读：

- [科目体系与核算维度设计教程](01_finance/chart-of-accounts-dimensions-guide.md)
- [金蝶财务配置指南](01_finance/kingdee-finance-configuration-guide.md)
- [财务基础资料与初始化](01_finance/master-data-and-initialization.md)
- [多组织、多账簿与集团核算教程](01_finance/multi-org-multi-book-accounting-guide.md)
- [国外财务与国际化核算专题：多币别、多准则、税务和合并](01_finance/international-finance-accounting-guide.md)
- [集团合并报表、内部交易抵消与内部往来对账专题](01_finance/consolidated-reporting-elimination-guide.md)
- [集团管理分析、事业部利润与内部转移定价专题](01_finance/group-management-profit-transfer-pricing-guide.md)
- [经营分析月报样例：事业部利润、产品毛利、客户贡献与预算执行](01_finance/management-analysis-monthly-report-sample-guide.md)

要形成的配置理解：

| 对象 | 学习重点 | 常见错误 |
| --- | --- | --- |
| 核算组织 | 组织边界、业务组织和财务组织关系 | 业务组织能做单，但财务组织或账簿没有配置完整 |
| 账簿 | 会计政策、期间、币别、启用期间 | 上线后才发现账簿期间、币别或会计政策选错 |
| 国际化核算 | 海外法人、本位币、IFRS/US GAAP、VAT/GST、预提税 | 把海外主体按国内单账簿单税制处理 |
| 科目 | 科目级次、余额方向、核算维度、受控系统 | 科目挂错维度，导致后续报表和对账都很痛苦 |
| 核算维度 | 客户、供应商、部门、项目、物料等 | 把应该做维度的内容做成明细科目，后期无法灵活分析 |
| 凭证模板 | 来源单据、取数规则、摘要、科目、维度 | 金额或维度取错，导致总账和业务账不一致 |

实操练习：

1. 设计一套简化科目表：现金、银行、应收、应付、收入、成本、费用、税金。
2. 为应收账款配置客户核算维度，为管理费用配置部门核算维度。
3. 用一笔销售业务验证凭证模板是否能正确带出客户、部门、税额和摘要。
4. 做一张初始化检查表，包含科目余额、客户余额、供应商余额、固定资产卡片和银行余额。
5. 设计一个两家公司集团样例，列出合并范围、内部往来科目、内部客户供应商和抵消事项。
6. 设计一个海外子公司核算样例，列出本位币、交易币别、当地税码、预提税、集团科目映射和报表折算口径。
7. 设计一张事业部利润表样例，列出收入、成本、内部交易、直接费用、分摊费用和管理利润。
8. 编一页经营分析月报摘要，至少包含事业部利润、产品毛利、客户贡献、预算偏差和异常事项。

验收标准：

- 能解释为什么“客户”不应该随意做成科目明细。
- 能根据一个管理报表需求判断该加科目、加维度、加辅助属性还是加报表口径。
- 能知道期初导入前必须先锁定哪些基础资料。

### 第三阶段：日常操作和月结闭环

先读：

- [金蝶财务日常操作手册](01_finance/finance-daily-operation-guide.md)
- [从业务单据到财务凭证：通俗学习手册](01_finance/business-document-to-voucher-learning-guide.md)
- [收入确认、合同履约与开票回款跨期专题](01_finance/revenue-recognition-contract-invoice-guide.md)
- [发票税务申报勾稽、红字和未开票收入专题](01_finance/tax-declaration-invoice-reconciliation-guide.md)
- [总账](01_finance/general-ledger.md)
- [凭证生成与常见分录](01_finance/voucher-generation-and-entries.md)
- [应收款管理](01_finance/accounts-receivable.md)
- [应收账龄、催收与坏账准备学习手册](01_finance/ar-aging-collection-bad-debt-guide.md)
- [应付款管理](01_finance/accounts-payable.md)
- [出纳与资金](01_finance/cashier-and-funds.md)
- [银企直连、票据与资金计划专题](01_finance/bank-enterprise-bills-funds-guide.md)
- [固定资产](01_finance/fixed-assets.md)
- [预算执行分析、占用释放与费用报销联动专题](01_finance/budget-execution-control-analysis-guide.md)
- [费用报销、借款还款与付款学习手册](01_finance/expense-reimbursement-funds-learning-guide.md)
- [月结流程](01_finance/month-end-close.md)
- [月结作战手册](01_finance/month-end-close-playbook.md)

日常操作主线：

| 时间 | 动作 | 金蝶关注点 | 证据 |
| --- | --- | --- | --- |
| 每天 | 检查业务单据审核、凭证生成失败、资金流水 | 单据状态、凭证生成情况、银行日记账 | 异常清单、处理记录 |
| 每周 | 往来核销、暂估检查、费用报销归集 | 应收应付余额、未核销单据、费用维度 | 往来账龄、未核销明细 |
| 月末前 | 存货核算、折旧、成本结转、税金计提 | 业务模块是否全部关账 | 月结前检查表 |
| 月末 | 生成凭证、过账、结转损益、报表取数 | 总账期间、凭证状态、报表公式 | 凭证清单、科目余额表 |
| 月末后 | 对账、归档、差异复盘 | 总账与业务账、报表与明细账 | 对账表、月结报告 |

实操练习：

1. 做一张手工凭证并审核、过账、反过账、反审核，记录每一步影响。
2. 做一笔应收收款核销，检查客户往来余额变化。
3. 做一笔应付付款核销，检查供应商往来余额变化。
4. 从一张采购入库单追到应付单、付款单、核销记录和凭证。
5. 从一张销售出库单追到应收单、收款单、成本凭证和客户余额。
6. 做一次收入确认跨期练习，区分出库、签收、开票、收款和收入确认。
7. 输出一次应收账龄和催收清单，检查未核销收款、逾期客户和坏账准备口径。
8. 做一笔银企付款、银行回写和银行对账，区分付款单审核成功和银行支付成功。
9. 做一笔员工借款、费用报销、付款和还款，检查员工往来余额。
10. 做一次预算执行测试：申请占用、报销消耗、差额释放、超预算审批和预算调整。
11. 做一次税务申报勾稽，核对销项、进项、红字、未开票收入和总账税金科目。
12. 把预算执行差异写入经营月报，说明是收入不足、成本超支、费用超预算还是资本占用过高。
13. 完成一次固定资产新增、计提折旧、生成凭证。
14. 模拟月结：凭证生成、凭证检查、过账、结转损益、报表取数。

验收标准：

- 能说清月结卡在哪一步，应该找业务、财务、开发还是运维。
- 能区分“数据没做完、配置不完整、权限不够、单据状态不对、二开逻辑异常”。
- 能拿出一份月结证据包。

## 路线二：实施顾问从调研到验收

适合对象：实施顾问、项目经理、交付负责人、内部信息化负责人。

目标：能把金蝶项目从调研、蓝图、配置、数据、测试、培训、上线和验收完整推进，并留下可复用交付物。

先读：

- [实施方法与交付](04_implementation/README.md)
- [金蝶实施交付作战手册](04_implementation/implementation-delivery-playbook.md)
- [项目调研与蓝图设计详细教程](04_implementation/project-research-and-blueprint-guide.md)
- [主数据与初始化详细教程](04_implementation/master-data-and-initialization-guide.md)
- [权限、角色与内控实施教程](04_implementation/permission-role-control-guide.md)
- [权限审计、关键岗位内控与越权操作追溯专题](04_implementation/permission-audit-sod-control-guide.md)
- [测试、培训与上线演练教程](04_implementation/testing-training-drill-guide.md)
- [上线切换、验收与运维移交教程](04_implementation/go-live-acceptance-handover-guide.md)

实施顾问要形成的工作闭环：

| 阶段 | 关键问题 | 必须落地的文档 | 失败信号 |
| --- | --- | --- | --- |
| 启动 | 范围、角色、计划、升级机制是否清楚 | 项目章程、计划、通讯录、风险清单 | 需求都说重要，但没人负责确认 |
| 调研 | 现状流程、痛点、报表、系统边界是否清楚 | 调研纪要、现状流程、需求清单 | 只记菜单，不记录业务规则 |
| 蓝图 | 未来流程能否用真实场景走通 | 蓝图方案、配置方案、数据方案 | 关键用户没有签字确认 |
| 配置 | 参数、单据、审批、凭证模板是否和蓝图一致 | 配置清单、变更记录 | 顾问凭记忆配置，没有记录 |
| 数据 | 主数据和期初能否对账 | 导入模板、校验报告、对账报告 | 只看导入成功，不看业务正确 |
| 测试 | 端到端流程、异常流程、权限、报表是否通过 | 测试用例、缺陷台账、测试报告 | 只测正常流程，不测退货、红冲、反审核 |
| 培训 | 用户能否独立操作 | 岗位手册、签到、练习题、FAQ | 培训变成演示，用户没有动手 |
| 上线 | 切换窗口、冻结点、应急方案是否明确 | 上线方案、应急预案、上线报告 | 上线当天还在改基础资料 |
| 验收 | 交付物、遗留问题、运维移交是否完整 | 验收报告、移交清单、归档目录 | 项目上线了，但知识都在个人脑子里 |

实操练习：

1. 选一家制造或商贸企业，写一份端到端蓝图：采购到付款、销售到收款、库存到成本、总账到报表。
2. 给财务、采购、仓库、销售、生产各设计 5 条测试用例。
3. 建一个权限审计包，包含用户角色清单、高危权限清单、职责分离冲突表和临时权限台账。
4. 建一个上线切换清单，明确冻结时间、责任人、回退策略和验收口径。

验收标准：

- 能把一个业务需求拆成流程、配置、数据、权限、报表、接口、测试几个维度。
- 能识别“客户想要一个字段”背后到底是查询、控制、报表、审批还是接口需求。
- 能判断哪些权限必须上线前收紧，哪些临时权限必须设置有效期和回收记录。
- 能在上线前判断哪些问题必须解决，哪些问题可以进入遗留清单。

## 路线三：供应链顾问掌握业务到财务衔接

适合对象：采购、销售、仓库、供应链顾问、财务成本会计。

目标：能理解采购、销售、库存、存货核算和财务凭证之间的关系，能处理常见库存和成本差异。

先读：

- [供应链知识区](02_supply-chain/README.md)
- [供应链核心操作教程](02_supply-chain/supply-chain-core-operation-guide.md)
- [供应链基础通俗入门：采购、销售、库存和存货核算](02_supply-chain/supply-chain-starter-plain-language-guide.md)
- [供应链单据流通俗学习手册](02_supply-chain/supply-chain-document-flow-learning-guide.md)
- [价格、信用、批号、盘点与暂估专题](02_supply-chain/price-credit-batch-counting-estimate-guide.md)
- [采购管理详细教程](02_supply-chain/purchase-management-guide.md)
- [采购结算、到票、暂估冲回与采购价差专题](02_supply-chain/purchase-settlement-invoice-variance-guide.md)
- [销售管理详细教程](02_supply-chain/sales-management-guide.md)
- [销售退货、红冲、退款与折让专题](02_supply-chain/sales-return-red-invoice-refund-guide.md)
- [客户退货质检、RMA、返修与报废专题](02_supply-chain/customer-return-quality-rma-guide.md)
- [客户索赔、售后备件、保内保外维修专题](02_supply-chain/after-sales-claims-spare-parts-guide.md)
- [渠道售后、服务站库存与经销商代修专题](02_supply-chain/channel-after-sales-service-station-guide.md)
- [库存管理详细教程](02_supply-chain/inventory-management-guide.md)
- [寄售、VMI 与客户寄售库存专题](02_supply-chain/consignment-vmi-inventory-guide.md)
- [存货核算详细教程](02_supply-chain/inventory-costing-guide.md)
- [存货成本差异、异常成本与库存关账专题](02_supply-chain/inventory-cost-variance-close-guide.md)
- [组织间结算详细教程](02_supply-chain/intercompany-settlement-guide.md)
- [供应链官方资料精读：协同、主数据和监控](02_supply-chain/supply-chain-official-source-digest.md)

必须理解的链路：

| 业务链路 | 关键单据 | 财务影响 |
| --- | --- | --- |
| 采购到付款 | 采购订单、收料、入库、应付单、付款单 | 存货、暂估、应付、进项税 |
| 销售到收款 | 销售订单、发货、出库、应收单、收款单 | 收入、成本、应收、销项税 |
| 库存到成本 | 入库、出库、调拨、盘点、核算单据 | 存货余额、主营业务成本、差异 |
| 组织间交易 | 跨组织调拨、内部结算、内部应收应付 | 内部往来、内部收入成本、抵消基础 |

实操练习：

1. 做一次采购入库到应付付款，检查库存账、应付账和总账。
2. 做一次销售出库到应收收款，检查库存减少、成本结转、收入确认。
3. 画出采购到付款、销售到收款的单据流，标出哪一步影响业务流、实物流、资金流和成本流。
4. 测试一次采购价目表、销售价目表、信用控制、批号出库、盘点差异和暂估冲回。
5. 做一次采购结算：入库暂估、发票到票、暂估冲回、价差调整和供应商对账。
6. 模拟销售退货、红字应收、红字发票、客户退款和成本冲回，记录对库存、应收、税额和毛利的影响。
7. 模拟客户退货质检：退回待检、判定返修或报废、换货、红字应收、退款和客户对账。
8. 模拟一次售后备件出库、保外维修收费、客户赔偿和供应商索赔，检查收入、成本和往来。
9. 模拟渠道售后：服务站备件补货、经销商代修、旧件返还、服务费结算和保内保外判断。
10. 做一次寄售/VMI 练习，区分库存地点、所有权、消耗结算和应收应付时点。
11. 做一次存货月结：清负库存、核算出库成本、处理暂估价差、生成凭证并和总账对账。
12. 模拟负库存、无成本、暂估未冲回、红字出库，记录系统表现和处理方法。

验收标准：

- 能判断库存账差异是数量问题、成本问题、期间问题还是凭证问题。
- 能把供应链问题翻译成财务影响，而不是只停留在单据状态。

## 路线四：制造顾问掌握从 BOM 到成本

适合对象：生产计划、车间、制造顾问、成本会计。

目标：能理解 BOM、MRP、生产订单、领料、报工、完工、MES 回写、设备采集、委外、质量和制造成本的完整链路。

先读：

- [生产制造知识区](03_manufacturing/README.md)
- [生产制造核心教程](03_manufacturing/manufacturing-core-guide.md)
- [工程数据与 BOM 详细教程](03_manufacturing/engineering-data-bom-guide.md)
- [PLM-BOM 变更同步、工程变更与生产版本追溯专题](07_integrations/plm-bom-ecn-change-sync-guide.md)
- [MRP 与计划管理详细教程](03_manufacturing/mrp-planning-guide.md)
- [生产订单执行详细教程](03_manufacturing/production-order-execution-guide.md)
- [委外管理详细教程](03_manufacturing/outsourcing-management-guide.md)
- [委外采购协同、发料收料与加工费结算专题](03_manufacturing/outsourcing-cost-settlement-collaboration-guide.md)
- [制造成本核算详细教程](03_manufacturing/manufacturing-costing-guide.md)
- [车间执行与报工教程](03_manufacturing/shop-floor-execution-guide.md)
- [车间看板、MES 报工回写与设备数据采集专题](03_manufacturing/mes-shop-floor-dashboard-data-collection-guide.md)
- [制造模块官方资料精读](03_manufacturing/manufacturing-official-source-digest.md)

制造主线：

1. 物料、BOM、工艺路线、工作中心准备完整。
2. PLM 工程变更和 BOM 版本按生效策略同步到金蝶。
3. MRP 根据需求、库存、在途、在制、提前期生成计划建议。
4. 生产订单下达后形成领料、报工、完工、入库。
5. MES、条码终端或设备网关把现场开工、报工、质量、停机和产量回写到金蝶。
6. 成本会计按材料、人工、制造费用归集和分配。
7. 完工入库和成本结转影响存货和主营业务成本。

实操练习：

1. 建一个两层 BOM，跑一次 MRP，分析为什么生成或不生成建议。
2. 模拟一次 PLM 工程变更：新 BOM 版本、生效日期、旧料处理、生产订单影响分析和版本追溯。
3. 做一张生产订单，从领料、补料、退料、报工到完工入库。
4. 做一张委外订单，从用料清单、委外发料、供应商处材料、委外入库、加工费应付到委外入库核算。
5. 模拟材料价格变动，观察制造成本和出库成本的影响。
6. 设计一条 MES 回写链路：生产订单下发、工位扫码、设备采集、报工回写、质检、完工入库和日报工对账。

验收标准：

- 能解释 MRP 不出计划的原因：需求、库存、BOM、提前期、计划策略、时间范围。
- 能解释 PLM 工程变更对物料、BOM 版本、采购、生产订单、旧料库存和售后备件的影响。
- 能解释生产成本差异：材料耗用、替代料、报工、费用分摊、完工数量。
- 能解释委外成本差异：供应商处材料、补退料、加工费、质检返修、委外入库核算。
- 能解释 MES 看板与金蝶生产订单进度不一致时，应从报工状态、回写日志、工序映射、质量结果和完工入库逐层排查。

## 路线五：BOS/苍穹开发从配置到插件

适合对象：BOS 开发、二开工程师、技术顾问、会配置单据但想写插件的人。

目标：能读懂金蝶对象模型，完成表单扩展、单据转换、工作流、权限和插件开发，并能考虑财务和业务一致性。

先读：

- [BOS/插件/二开](05_development-bos/README.md)
- [苍穹开发者工作台与项目创建](05_development-bos/cangqiong-developer-portal-project.md)
- [苍穹单据与基础资料建模](05_development-bos/cangqiong-business-object-modeling.md)
- [BOS/苍穹开发实战教程](05_development-bos/bos-development-practice-guide.md)
- [插件开发、调试与发布教程](05_development-bos/plugin-development-debugging-guide.md)
- [插件治理、排障与上线回归手册](05_development-bos/plugin-governance-and-troubleshooting-guide.md)
- [BOS 插件源码级案例：保存校验、操作服务、单据转换与列表过滤](05_development-bos/plugin-code-cases-save-operation-conversion-guide.md)
- [单据转换、工作流与权限扩展教程](05_development-bos/workflow-bill-conversion-permission-guide.md)
- [BOS、业务流程与低代码官方资料精读](05_development-bos/bos-workflow-official-source-digest.md)

开发学习顺序：

1. 先会建对象：基础资料、单据、分录、字段、枚举、引用基础资料。
2. 再会改界面：布局、字段属性、操作按钮、列表过滤、默认值。
3. 再会做流转：单据转换、源单关联、字段携带、数量反写。
4. 再会加控制：校验规则、保存插件、提交审核控制、权限控制。
5. 再会看案例：保存前校验、审核后日志、下推字段补齐、列表按用户过滤。
6. 最后会治理和排查：幂等、事务、日志、性能、发布、回滚、回归测试。

必须养成的习惯：

- 涉及金额、税额、数量、库存、凭证的二开，必须先确认业务规则和财务影响。
- 新增字段要检查列表、查询、打印、接口、凭证模板、报表和权限。
- 插件报错要保留完整堆栈、单据编号、用户、组织、时间、操作按钮。
- 源码级案例要先改成当前版本可编译代码，再谈生产发布；不要把结构示例当成环境已验证实现。

验收标准：

- 能从业务需求判断是配置、单据转换、工作流、插件还是接口。
- 能写出一次发布的回归测试范围。
- 能说明二开为什么会影响月结或对账。

## 路线六：数据、SQL、BI 与报表排查

适合对象：报表开发、数据分析、BI 顾问、实施顾问、技术支持、财务分析。

目标：能建立“业务对象 -> 单据 -> 数据表 -> 报表口径 -> BI 指标 -> 经营动作”的追踪能力，避免直接用 SQL 猜业务，也避免把 BI 做成漂亮但不可复核的图表。

先读：

- [数据模型与 SQL](06_data-model-sql/README.md)
- [数据模型与 SQL 查询作战手册](06_data-model-sql/data-query-playbook.md)
- [金蝶数据模型阅读方法](06_data-model-sql/kingdee-data-model-reading-guide.md)
- [核心表字典与常用 SQL 查询包](06_data-model-sql/core-table-dictionary-and-sql-pack.md)
- [真实环境已验证 SQL 示例库](06_data-model-sql/real-environment-verified-sql-library.md)
- [财务对账与 SQL 排查教程](06_data-model-sql/finance-reconciliation-sql-guide.md)
- [供应链与库存数据排查教程](06_data-model-sql/supply-chain-inventory-sql-guide.md)
- [报表取数、指标口径与数据分析教程](06_data-model-sql/reporting-metrics-data-analysis-guide.md)
- [BI 分析体系详解：指标、模型、看板、权限和经营洞察](06_data-model-sql/bi-analytics-system-guide.md)
- [金蝶 ChatBI 实战专题：自然语言问数、口径解释与经营驾驶舱](06_data-model-sql/kingdee-chatbi-practical-guide.md)

数据排查原则：

| 原则 | 说明 |
| --- | --- |
| 先业务后 SQL | 先确认组织、期间、单据状态、币别、审核状态，再写 SQL |
| 先系统报表后底表 | 先用标准报表确认差异，再下钻到底表 |
| 先口径后结果 | 不同报表可能按不同日期、组织、状态取数 |
| 只读优先 | 排查阶段不直接改库，必须保留查询条件和证据 |
| 版本相关 | 表结构、字段名、业务逻辑可能随版本和补丁变化 |
| BI 要能下钻 | 经营指标必须能追到维度、明细单据和责任动作 |
| ChatBI 要能解释 | 自然语言答案必须显示公式、来源、过滤条件、权限和更新时间 |

实操练习：

1. 从一张凭证反查来源单据，再定位单据头、分录和基础资料。
2. 复现一个总账与应收不一致的问题，写清楚报表口径和过滤条件。
3. 做一张库存差异排查表，按物料、仓库、批号、期间和单据状态拆解。
4. 选 5 个常用 SQL 模板，替换成当前环境真实表名字段，并记录前台验证结果。
5. 从真实问题里沉淀 3 条 SQL 记录卡，至少覆盖单据状态、凭证生成和接口或库存差异。
6. 设计一份 BI 指标字典，至少覆盖销售额、毛利率、库存周转、逾期应收和预算执行率。
7. 画一个老板驾驶舱草图，要求每个指标都能说明数据来源、口径和下钻路径。
8. 为销售毛利、逾期应收、呆滞库存和预算执行各写 3 条 ChatBI 标准问法，并写出必须澄清的模糊问法。

验收标准：

- 能写一份 SQL 笔记，包含目的、口径、风险、过滤条件和样例结果。
- 能解释为什么两张报表金额不同，而不是直接说系统错了。
- 能把常用查询整理成可复核的查询包，而不是散落在聊天记录和临时文件里。
- 能区分 template、env-ready、verified，不把未经前台核对的 SQL 当成生产结论。
- 能说明 BI 看板数字和标准报表不一致时，应该先查口径、权限、状态和日期，而不是先改图表。
- 能说明 ChatBI 问数结果需要怎样回到指标字典、标准报表、权限范围和源单明细复核。

## 路线七：接口、运维与问题处理

适合对象：接口开发、系统管理员、运维、技术支持、项目售后。

目标：能处理接口失败、权限异常、发布问题、性能问题和生产环境故障，并把处理过程沉淀成可复用案例。

先读：

- [接口与集成](07_integrations/README.md)
- [金蝶接口集成实施教程](07_integrations/integration-implementation-guide.md)
- [外部系统集成场景教程](07_integrations/external-system-integration-scenarios.md)
- [接口联调、监控、重试与对账教程](07_integrations/interface-debugging-monitoring-reconciliation.md)
- [税务平台、银企回单与接口批量补偿专题](07_integrations/financial-integration-tax-bank-compensation-guide.md)
- [WMS 出入库对账、接口补偿与库存一致性专题](07_integrations/wms-inventory-reconciliation-compensation-guide.md)
- [PLM-BOM 变更同步、工程变更与生产版本追溯专题](07_integrations/plm-bom-ecn-change-sync-guide.md)
- [WebAPI、集成平台与安全参数官方资料精读](07_integrations/webapi-integration-official-source-digest.md)
- [AI 文档分类与结构化提取](07_integrations/ai-document-classification.md)
- [金蝶 AI 应用专题：AI 管理助手、智能体与业务落地](07_integrations/kingdee-ai-agent-application-guide.md)
- [环境、发布和版本](08_environments-releases/README.md)
- [系统管理员日常运维教程](08_environments-releases/system-admin-daily-ops-guide.md)
- [备份、恢复、监控与性能巡检教程](08_environments-releases/backup-restore-monitoring-guide.md)
- [数据清理归档、接口报文留存与审计追溯专题](08_environments-releases/data-archive-log-retention-audit-guide.md)
- [问题排查与运维处理手册](09_operations-issues/issue-triage-and-operations-playbook.md)
- [全模块问题案例库](09_operations-issues/operations-case-library.md)

问题处理框架：

1. 先确定影响范围：单用户、单组织、单模块、全系统、接口批次还是某个版本后出现。
2. 再确定复现路径：用户、时间、菜单、单据编号、操作按钮、报错原文。
3. 再看系统证据：日志、接口报文、操作记录、审批记录、单据状态、权限分配。
4. 最后形成处理：临时绕行、根因修复、数据补偿、回归测试、预防措施。
5. 做清理归档前，先确认留存年限、附件、接口报文、操作日志和审计取证要求，避免清理后证据链断掉。
6. 做 AI 智能体或管理助手上线前，先确认知识来源、数据权限、工具权限、人工确认点、失败回滚和审计日志。
7. 做财务集成补偿前，先确认外部事实、金蝶单据、凭证、回单/发票附件和补偿批次报告。

验收标准：

- 能写出一份完整问题记录，而不是只保存一句“已处理”。
- 能把问题归因到配置、数据、权限、二开、接口、环境或产品限制。
- 能知道哪些操作需要先备份、先审批、先演练。
- 能判断 AI 场景是问答、生成、分析、审核还是执行，并设置对应的权限和人工确认点。
- 能区分接口重试和批量补偿，避免税务发票、银企付款、银行流水重复入账或重复付款。

## 30/60/90 天学习计划

### 前 30 天：能看懂系统

任务：

- 读完 [知识地图](knowledge-map.md)、[财务模块地图](01_finance/finance-module-map.md)、[供应链核心操作教程](02_supply-chain/supply-chain-core-operation-guide.md)。
- 在测试环境跑通采购到付款、销售到收款、凭证生成、总账查询。
- 记录 10 个不懂的菜单、字段或参数，按规范写进 `00_inbox/`。

成果：

- 一张端到端业务流程图。
- 一份岗位常用菜单清单。
- 一份基础问题清单。

### 第 31 到 60 天：能独立处理日常

任务：

- 深读总账、应收、应付、库存、存货核算、月结、常见问题。
- 完成一次模拟月结和一次往来对账。
- 选 3 个真实问题，按问题模板写完整记录。

成果：

- 一份月结检查表。
- 一份对账差异分析表。
- 三篇问题处理记录。

### 第 61 到 90 天：能优化和带人

任务：

- 梳理本公司实际配置、权限、凭证模板、报表和接口。
- 把高频问题反哺到模块文档和 FAQ。
- 设计一套新人培训路线和练习题。

成果：

- 一份本公司金蝶配置说明。
- 一份本公司岗位操作手册。
- 一份培训计划和练习题。

## 每周维护节奏

| 时间 | 动作 | 产出 |
| --- | --- | --- |
| 周一 | 整理上周新增问题 | FAQ 或问题处理记录 |
| 周二 | 补一篇模块实操内容 | 模块教程更新 |
| 周三 | 复盘一个报表或 SQL 口径 | 数据区笔记 |
| 周四 | 整理一个项目交付物 | 实施区或模板区更新 |
| 周五 | 回看知识地图和入口 | 更新导航、索引和首页 |
