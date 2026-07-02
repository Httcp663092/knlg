# 知识库缺口与补充路线图

<!-- NAV_START -->
> **快捷目录**
>
> [界面首页](../index.html) | [文档首页](README.md) | [知识地图](knowledge-map.md) | [学习路径](learning-paths.md) | [财务](01_finance/README.md) | [供应链](02_supply-chain/README.md) | [制造](03_manufacturing/README.md) | [实施](04_implementation/README.md) | [开发](05_development-bos/README.md) | [数据](06_data-model-sql/README.md) | [集成](07_integrations/README.md) | [运维](09_operations-issues/README.md) | [问题](10_common-questions/README.md) | [资料](90_references/README.md)
>
> 上一章：[金蝶知识库学习路径](learning-paths.md) | 下一章：[记录规范](conventions.md) | [本章目录](README.md)
<!-- NAV_END -->






这页用于回答一个长期问题：知识库已经很多了，下一步到底缺什么、先补什么、怎么判断补得够不够。

当前知识库已经覆盖财务、供应链、制造、实施、开发、数据、集成、运维和问题库，基础框架已经成型。后续维护不应再只增加泛泛目录，而要优先补“项目中经常卡月结、卡验收、卡对账、卡培训”的深水区。

## 一、当前覆盖判断

| 区域 | 当前状态 | 说明 |
| --- | --- | --- |
| 财务基础 | 已加厚 | 总账、凭证、应收应付、月结、报表、现金流、费用、税务、档案都有独立页，并已补财务通俗入门入口 |
| 应收风险 | 已加深 | 已有账龄、催收、坏账准备专题 |
| 供应链主流程 | 已加厚 | 采购、销售、库存、存货核算、单据流、价格信用批号盘点暂估都有内容，并已补供应链通俗入门入口 |
| 供应链反向业务 | 已加深 | 已有销售退货、红冲、退款、折让、客户退货质检、RMA、返修、报废、售后索赔、备件、渠道售后、服务站库存和经销商代修专题 |
| 供应链特殊库存 | 已加深 | 已有寄售、VMI、客户寄售、消耗结算和特殊库存对账专题 |
| 制造 | 已加深 | BOM、MRP、生产订单、委外、委外发料收料、加工费结算、成本、质量、车间报工、MES 回写、设备采集和车间看板已有专题 |
| 实施交付 | 已加深 | 调研、蓝图、主数据、权限、权限审计、职责分离、测试、上线验收都有闭环 |
| BOS/开发 | 已加深 | 建模、插件、流程、权限、插件治理和源码级插件案例已有，后续适合按真实代码继续升级 |
| 数据 SQL / BI | 已加深 | 有阅读方法、核心表字典、常用查询包、真实环境 SQL 示例库、对账/库存排查、BI 分析体系、ChatBI 问数实战和真实环境内容收集入口，后续可继续把实际项目 SQL、BI 指标和 ChatBI 问答标记为 verified |
| 集成运维 | 已加深 | WebAPI、集成、监控、重试、税务平台发票同步、银企回单、接口批量补偿、WMS 出入库对账、PLM-BOM 工程变更、AI 文档分类、AI 管理助手/智能体、库存一致性和运维案例已有，后续可按真实报文继续升级 |

## 二、模块缺口快速盘点

这次从“文件数量、内容厚度、项目风险、是否已形成专题”四个角度看，后续还值得继续补这些模块：

| 模块 | 当前短板 | 建议补法 |
| --- | --- | --- |
| 供应链 | 主流程已厚，商贸分销、渠道售后、服务站库存、经销商代修已补，跨境退货和连锁零售还可继续拆 | 后续补跨境退货、连锁零售、服务绩效和大客户驻场备件 |
| 实施交付 | 权限基础已有，审计证据包和高危权限追溯原来偏薄 | 已补权限审计专题，后续可按真实客户权限导出做案例 |
| 集成 | WebAPI、通用集成、WMS 出入库对账、PLM-BOM 工程变更、税务平台、银企和接口批量补偿已补 | 后续按真实接口报文、失败日志、补偿批次和月结证据包升级 |
| 环境运维 | 基础运维已有，容量治理、归档、日志留存和审计追溯已开始加厚 | 已补数据清理归档、接口报文留存和审计追溯，后续按真实清理规则、日志策略和发布审计继续升级 |
| BOS/开发 | 插件治理和源码级结构案例已有 | 后续按真实保存插件、操作服务插件、单据转换插件和列表插件继续升级 |
| 财务扩展 | 财务基础很厚，预算执行、税务申报、集团管理分析、国外财务和经营月报样例已补 | 后续按真实经营分析月报、预算执行报表、海外子公司税码和费用分摊案例继续升级 |
| 数据 SQL / BI | 示例库、BI 体系和 ChatBI 实战已有，但还缺真实客户验证样本 | 后续拿真实单号、截图、报表条件、BI 指标字典、ChatBI 问答记录和看板截图后升级为 verified |

## 三、P0：优先继续加厚

P0 是“项目里最容易出事，且能马上提高知识库实用性”的内容。

| 缺口 | 为什么优先 | 当前处理 |
| --- | --- | --- |
| 存货成本差异、异常成本和库存关账 | 月结最常卡在库存、存货核算、凭证和总账差异；顾问和财务都需要排查路径 | 已新增 [存货成本差异、异常成本与库存关账专题](02_supply-chain/inventory-cost-variance-close-guide.md) |
| 银企、票据、资金计划 | 出纳日常、付款安全、银行对账、票据到期和资金预测都容易散落在口头经验里 | 已新增 [银企直连、票据与资金计划专题](01_finance/bank-enterprise-bills-funds-guide.md) |
| 收入确认、合同履约和开票回款跨期 | 销售出库、应收、发票、收入、成本、税务跨期时容易出现管理口径和财务口径差异 | 已新增 [收入确认、合同履约与开票回款跨期专题](01_finance/revenue-recognition-contract-invoice-guide.md) |
| 采购结算、到票、暂估冲回和价差 | 暂估已经有内容，但采购到票差异、费用分摊和供应商对账还可以更细 | 已新增 [采购结算、到票、暂估冲回与采购价差专题](02_supply-chain/purchase-settlement-invoice-variance-guide.md) |
| 数据表字典和常用 SQL 查询包 | 现有 SQL 内容偏方法论，还缺更多可直接套用的查询清单 | 已新增 [核心表字典与常用 SQL 查询包](06_data-model-sql/core-table-dictionary-and-sql-pack.md) |
| 真实环境已验证 SQL 示例库 | 从实际单号、报表差异、接口日志和成本对账中沉淀已验证查询，并标明前台验证入口 | 已新增 [真实环境已验证 SQL 示例库](06_data-model-sql/real-environment-verified-sql-library.md) |
| 委外采购协同、发料收料和加工费结算 | 委外同时牵涉计划、采购、库存、质检、应付和成本，基础教程之外需要完整对账和结算专题 | 已新增 [委外采购协同、发料收料与加工费结算专题](03_manufacturing/outsourcing-cost-settlement-collaboration-guide.md) |
| 车间看板、MES 报工回写与设备数据采集 | 生产现场最容易出现 MES 已完成、金蝶未回写、设备数量和报工数量不一致、看板进度失真的问题 | 已新增 [车间看板、MES 报工回写与设备数据采集专题](03_manufacturing/mes-shop-floor-dashboard-data-collection-guide.md) |
| 真实环境内容收集入口 | 截图、报错、SQL、菜单路径和单据证据如果没有统一入口，很容易散在聊天记录和临时文件里 | 已新增 [真实环境内容收集与沉淀清单](00_inbox/real-environment-content-intake.md) |
| 权限审计、关键岗位内控与越权操作追溯 | 权限基础配置之外，项目验收和审计最常卡在高危权限、冲突岗位、临时授权、反审核反结账和敏感操作证据 | 已新增 [权限审计、关键岗位内控与越权操作追溯专题](04_implementation/permission-audit-sod-control-guide.md) |
| 客户退货质检、RMA、返修与报废 | 销售退货不只是红冲退款，还要处理退货授权、待检库存、质量判定、返修、报废和客户对账 | 已新增 [客户退货质检、RMA、返修与报废专题](02_supply-chain/customer-return-quality-rma-guide.md) |
| 客户索赔、售后备件、保内保外维修 | 售后业务会牵涉免费备件、收费维修、客户赔偿、供应商索赔、维修收入和售后成本 | 已新增 [客户索赔、售后备件、保内保外维修专题](02_supply-chain/after-sales-claims-spare-parts-guide.md) |
| 集团合并报表、内部交易抵消与内部往来对账 | 多组织项目如果只做个别账，月末合并会卡在内部往来、内部利润和权益抵消 | 已新增 [集团合并报表、内部交易抵消与内部往来对账专题](01_finance/consolidated-reporting-elimination-guide.md) |
| 发票税务申报勾稽、红字和未开票收入 | 月末申报最常卡在销项、进项、红字、未开票收入、已开票未收入和总账税金科目不一致 | 已新增 [发票税务申报勾稽、红字和未开票收入专题](01_finance/tax-declaration-invoice-reconciliation-guide.md) |
| 渠道售后、服务站库存和经销商代修 | 售后备件放在服务站、经销商代修、旧件返还和服务费结算如果不入系统，库存、成本和客户满意度都会失真 | 已新增 [渠道售后、服务站库存与经销商代修专题](02_supply-chain/channel-after-sales-service-station-guide.md) |
| WMS 出入库对账、接口补偿与库存一致性 | 仓库现场执行在 WMS，财务库存和成本在金蝶，接口回写、重复单、补偿和库存状态不一致会直接影响月结 | 已新增 [WMS 出入库对账、接口补偿与库存一致性专题](07_integrations/wms-inventory-reconciliation-compensation-guide.md) |
| 集团管理分析、事业部利润与内部转移定价 | 合并报表解决对外口径，但管理层还需要事业部、产品线、客户、渠道和项目利润；内部转移价和费用分摊如果不清，经营分析会失真 | 已新增 [集团管理分析、事业部利润与内部转移定价专题](01_finance/group-management-profit-transfer-pricing-guide.md) |
| 预算执行分析、占用释放与费用报销联动 | 预算项目常卡在申请占用、报销消耗、作废释放、超预算审批和总账口径不一致 | 已新增 [预算执行分析、占用释放与费用报销联动专题](01_finance/budget-execution-control-analysis-guide.md) |
| PLM-BOM 变更同步、工程变更与生产版本追溯 | 工程变更影响物料、BOM、采购、MRP、生产订单、旧料、成本和售后备件，PLM 与金蝶边界必须清楚 | 已新增 [PLM-BOM 变更同步、工程变更与生产版本追溯专题](07_integrations/plm-bom-ecn-change-sync-guide.md) |
| BOS 源码级插件案例：保存校验、操作服务、单据转换与列表过滤 | 开发排障时不能只讲治理原则，还要能看见保存前校验、审核后处理、下推字段补齐和列表过滤的代码结构 | 已新增 [BOS 插件源码级案例：保存校验、操作服务、单据转换与列表过滤](05_development-bos/plugin-code-cases-save-operation-conversion-guide.md) |
| 数据清理归档、接口报文留存与审计追溯 | 生产运行久了以后，历史单据、附件、接口报文和操作日志会同时牵涉容量、性能、合规和审计取证 | 已新增 [数据清理归档、接口报文留存与审计追溯专题](08_environments-releases/data-archive-log-retention-audit-guide.md) |
| 经营分析月报样例 | 管理层不只要报表，还要知道利润、毛利、客户贡献、预算偏差和异常事项之间的因果关系 | 已新增 [经营分析月报样例：事业部利润、产品毛利、客户贡献与预算执行](01_finance/management-analysis-monthly-report-sample-guide.md) |
| 财务和供应链通俗基础 | 内容已经很厚，但新人需要更低门槛入口，把业务、单据、库存、应收应付、凭证和报表串起来 | 已新增 [财务基础通俗入门](01_finance/finance-starter-plain-language-guide.md) 和 [供应链基础通俗入门](02_supply-chain/supply-chain-starter-plain-language-guide.md) |
| 商贸分销行业场景 | 商贸分销项目常卡在价格、信用、发货、回款、返利、渠道库存和客户对账，必须按行业场景串起来 | 已新增 [商贸与分销行业场景包](02_supply-chain/trading-distribution-scenario-pack.md) |
| BI 分析体系、指标字典和经营驾驶舱 | 经营分析不能只停留在月报样例，还需要指标体系、数据模型、权限、看板和 ChatBI 使用边界 | 已新增 [BI 分析体系详解：指标、模型、看板、权限和经营洞察](06_data-model-sql/bi-analytics-system-guide.md) |
| ChatBI 自然语言问数、口径解释和权限验收 | 业务人员开始用自然语言问数后，最容易出现口径不清、问题太宽、越权和无法复核 | 已新增 [金蝶 ChatBI 实战专题：自然语言问数、口径解释与经营驾驶舱](06_data-model-sql/kingdee-chatbi-practical-guide.md) |
| 金蝶 AI 管理助手、智能体和业务落地 | 金蝶 AI 不只是文档分类，还涉及知识库、RAG、工具调用、人工确认、权限脱敏和审计 | 已新增 [金蝶 AI 应用专题：AI 管理助手、智能体与业务落地](07_integrations/kingdee-ai-agent-application-guide.md) |
| 税务平台、银企回单与接口批量补偿 | 财务集成最怕外部已成功、金蝶未回写，或补偿后重复付款、重复开票、重复入账 | 已新增 [税务平台、银企回单与接口批量补偿专题](07_integrations/financial-integration-tax-bank-compensation-guide.md) |
| 国外财务、多币别、多准则和跨境税务 | 海外主体会同时牵涉当地准则、IFRS/US GAAP、VAT/GST/Sales Tax、预提税、转移定价、合并报表和外币折算 | 已新增 [国外财务与国际化核算专题](01_finance/international-finance-accounting-guide.md) |

## 四、P1：下一阶段加深

| 缺口 | 应补内容 |
| --- | --- |
| 渠道售后和服务站库存 | 已新增 [渠道售后、服务站库存与经销商代修专题](02_supply-chain/channel-after-sales-service-station-guide.md)，后续可按真实服务站盘点和经销商结算数据继续升级 |
| SQL 记录卡样例库二期 | 等拿到真实环境单号、截图、报表条件后，把 template SQL 升级为 verified 记录 |
| 集团管理分析 | 已新增 [集团管理分析、事业部利润与内部转移定价专题](01_finance/group-management-profit-transfer-pricing-guide.md) 和 [经营分析月报样例](01_finance/management-analysis-monthly-report-sample-guide.md)，后续可按真实经营月报继续升级 |
| 预算执行分析 | 已新增 [预算执行分析、占用释放与费用报销联动专题](01_finance/budget-execution-control-analysis-guide.md)，后续可按真实预算执行报表继续升级 |
| 发票税务申报勾稽 | 已新增 [发票税务申报勾稽、红字和未开票收入专题](01_finance/tax-declaration-invoice-reconciliation-guide.md)，后续可按真实税务平台导出字段继续升级 |
| 权限审计二期 | 等拿到真实用户角色导出、操作日志和审计问题后，把模板升级成已验证审计案例 |
| 源码级插件二期 | 已新增 [BOS 插件源码级案例](05_development-bos/plugin-code-cases-save-operation-conversion-guide.md)，后续可按真实仓库代码、真实字段标识和可编译插件继续升级 |
| 数据归档审计二期 | 已新增 [数据清理归档、接口报文留存与审计追溯专题](08_environments-releases/data-archive-log-retention-audit-guide.md)，后续可按真实清理规则、接口日志表和审计抽样要求继续升级 |
| BI 二期 | 已新增 [BI 分析体系详解](06_data-model-sql/bi-analytics-system-guide.md) 和 [金蝶 ChatBI 实战专题](06_data-model-sql/kingdee-chatbi-practical-guide.md)，后续可按真实指标字典、驾驶舱截图、ChatBI 问答记录和标准报表核对结果继续升级 |
| AI 智能体二期 | 已新增 [金蝶 AI 应用专题](07_integrations/kingdee-ai-agent-application-guide.md)，后续可按真实知识库、真实智能体工具调用日志、人工确认记录和审计样本继续升级 |
| 财务集成补偿二期 | 已新增 [税务平台、银企回单与接口批量补偿专题](07_integrations/financial-integration-tax-bank-compensation-guide.md)，后续可按真实发票平台回写、银企回单、银行流水和补偿批次继续升级 |
| 国际化财务二期 | 已新增 [国外财务与国际化核算专题](01_finance/international-finance-accounting-guide.md) 和 [海外子公司建账与月结实操包](01_finance/overseas-subsidiary-close-implementation-pack.md)，后续可按真实海外子公司、真实税码、真实报表包和合并调整继续升级 |

## 五、P2：有价值但可稍后

| 缺口 | 应补内容 |
| --- | --- |
| PLM / WMS 深度集成 | WMS 出入库对账和 PLM-BOM 变更同步已补，后续可按真实接口报文和字段映射升级 |
| BI 经营分析 | 已补 BI 体系页和 ChatBI 实战页，后续补真实销售毛利、库存周转、采购价格、客户回款、制造效率看板和 ChatBI 追问样例 |
| AI 管理助手 | 已补 AI 应用落地页，后续补真实知识库问答、报销审核、采购助手和实施助手样例 |
| 更多源码级插件案例 | 已补结构案例，后续补真实代码、真实字段、真实测试用例 |
| 数据清理和归档策略 | 已补治理专题，后续补真实清理规则、附件归档脚本、日志留存参数和审计样例 |
| 行业场景包 | 已新增 [商贸与分销行业场景包](02_supply-chain/trading-distribution-scenario-pack.md)，后续继续补制造、项目型、连锁零售、医药批号、食品保质期等 |

## 六、后续维护原则

每轮维护建议只做 2-3 个专题，不要一次铺太散。

| 原则 | 做法 |
| --- | --- |
| 先补高频痛点 | 优先选月结、对账、成本、资金、安全、上线验收这些会卡项目的内容 |
| 每篇都要能落地 | 至少包含流程、对象、检查表、案例、排查路径和参考链接 |
| 新页必须可发现 | 同步更新首页、知识地图、学习路径、模块 README 和参考资料索引 |
| 引用要能复核 | 官方资料链接集中沉淀到 `90_references/official-links.md` |
| 每轮都要校验 | 跑本地链接检查、`git diff --check`，再提交推送 |

## 七、下一轮建议

如果继续深耕，建议下一轮补：

1. `真实源码级插件二期：把当前仓库里的保存插件、操作服务插件、单据转换插件改写成已验证案例`
2. `真实数据归档二期：按生产清理规则、附件策略、接口日志表和审计抽样要求升级专题`
3. `真实 BI 二期：用实际指标字典、老板驾驶舱、销售/采购/库存看板和 ChatBI 问答记录升级 BI 专题`
4. `真实 AI 二期：用知识库问答、报销审核、采购助手、实施助手和工具调用日志升级 AI 专题`
5. `真实经营分析月报二期：用实际报表模板、预算版本、事业部维度和异常清单升级样例`
6. `SQL 记录卡样例库二期：把真实单号、截图和报表条件沉淀成 verified`
7. `行业场景包二期：制造、项目型、连锁零售、医药批号、食品保质期`

采购结算、收入确认、寄售/VMI、委外协同、客户退货质检、售后索赔备件、渠道售后、商贸分销、合并报表、国外财务、海外子公司月结、集团管理分析、经营分析月报、财务和供应链通俗基础、BI 分析体系、ChatBI 问数实战、金蝶 AI 智能体、预算执行、税务申报勾稽、MES 车间数据、WMS 出入库对账、PLM-BOM 工程变更、权限审计、源码级插件结构案例、数据归档审计治理、真实环境收集入口、常用 SQL 查询包和真实环境 SQL 示例库补完后，财务、供应链、制造、实施、安全内控、开发、集成、运维、BI、AI 和数据排查之间已经形成更完整的项目作战图。下一步更适合进入真实代码、真实清理规则、真实经营月报、真实海外税码与报表包、真实 BI 看板、真实 AI 智能体样本，并在拿到真实单号和截图后把 SQL 模板升级成 verified 记录。
