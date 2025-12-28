# FE 课程报告备选主题

>Note (`2025/12/25 9:32`)：    
大家好，我会发布了一些选题，供大家参考和选择。大家可以先浏览一下，看看对哪一个选题感兴趣。我将于 12.26 日组织大家确认选题 (请预先申请一个 github.com 的账号，并 fork 本仓库)。 

- 有些文献的 PDF 链接对应的是 working paper 版本，大家可以根据需要自行寻找最终发表版本。
  - 【PDF】文件夹：存放了部分选题的 PDF 文档
- **下载**：部分论文的复现资料 - [点击查看](https://www.jianguoyun.com/p/DYgReTcQtKiFCBip6p4GIAA)
- **格式**：课程报告格式参考 - [Top论文复现及中文精要](https://www.jianguoyun.com/p/DVlZ9DYQtKiFCBil9O4EIAA)
  - 这是一些已经完成的复现报告，大家的课程报告基本上按此风格撰写即可。

---

[toc]

---

# T1. Wang-2024-EE

- Wang, Z., Zhang, T., Ren, X., & Shi, Y. (**2024**). AI adoption rate and corporate green innovation efficiency: Evidence from Chinese energy companies. **Energy Economics**, 132, 107499. [Link](https://doi.org/10.1016/j.eneco.2024.107499), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/2026-Spring/Wang_2024_AI_adoption_rate_and_corporate_green_innovation.pdf), [Google](<https://scholar.google.com/scholar?q=AI adoption rate and corporate green innovation efficiency: Evidence from Chinese energy companies>), [cited](https://scholar.google.com/scholar?cites=3084301341760475150&as_sdt=2005&sciodt=0,5&hl=zh-CN), [Replication](https://ars.els-cdn.com/content/image/1-s2.0-S014098832400207X-mmc1.zip)。
  - 该文只有一个 `.do` 文档和一个 `.dta` 文档，可以一键执行到底。

- **摘要**：人工智能（AI）技术的问世推动人类社会发展格局发生变革性转变。同时，绿色创新作为能源企业转型升级的核心驱动力，有望借助人工智能等前沿技术实现赋能发展。然而，现有学术研究对于能源企业人工智能技术采纳率与绿色创新之间的关联探讨较为匮乏。
本文基于2010—2020年中国能源行业上市公司的面板数据展开实证分析，研究发现，人工智能技术采纳程度较高的能源企业，其绿色创新效率也相应处于更高水平。这一正向效应在积极参与环境、社会及治理（ESG）活动的企业中表现尤为显著。但研究同时揭示，管理层的短期利益导向会削弱人工智能技术采纳对绿色创新的促进作用。进一步的异质性分析表明，上述核心结论在**两职合一**（董事长与总经理由同一人担任）的能源企业、国有企业以及未持有银行股份的企业中具有更为显著的统计意义。
本文的研究结论不仅填补了现有文献的研究空白，还为政策制定者制定能源企业战略发展相关政策提供了全新的理论洞见与实践指导。


# T2. Cepni-2024-EE

Cepni, O., Şensoy, A., & Yılmaz, M. H. (**2024**). Climate change exposure and cost of equity. **Energy Economics**, 130, 107288. [Link](https://doi.org/10.1016/j.eneco.2023.107288), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/2026-Spring/Cepni_2024_Climate_change_exposure_and_cost_of_equity.pdf), [Google](<https://scholar.google.com/scholar?q=Climate change exposure and cost of equity>). [Replication](https://ars.els-cdn.com/content/image/1-s2.0-S0140988323007867-mmc1.zip)。

- 本文考察了企业面临的气候变化风险敞口与权益融资成本之间的关联关系。研究基于一套新颖的美国企业层面气候变化风险数据集，结果显示，2010—2021 年期间，企业的气候变化风险敞口越高，其权益融资成本也越高。其中，气候物理风险与政策监管风险对权益融资成本的影响相对微弱，而由新商业机会不确定性引致的气候转型风险，是驱动企业权益融资成本变动的核心作用机制。通过熵平衡法、工具变量回归、动态面板估计及双重差分模型等多种计量方法进行检验，本文结论有效缓解了内生性问题的干扰。进一步研究发现，对于气候议题关注度更高、气候变化感知程度更强以及融资约束问题更为突出的企业而言，气候变化风险敞口与权益融资成本之间的正向关联更为显著。

说明：
  - 该文的复现文档包含多个文件夹，分类放置了 .do 文件，数据文件和输出结果。数据处理过程涉及多个数据文件的合并。
  - 基准回归、稳健性检验、机制分析、内生性问题都做了一遍，没有太详细的论述

Stata 命令：

- `import excel`, `merge`, `append`, `duplicates`, `encode`
- `foreach`
- `winsor2`
- `statsby`
- `reghdfe`, `ppmlhdfe`
- `outreg2` 
- Oster (2019) 遗漏变量偏误检验


### 代码结构：非常规范

```dos
Cepni-2024-EE-xtabond2-DID-robust \
|-- cepni-2024-ee-中文精要.md
|-- cepni-2024-ee.ipynb
|-- cepni-2024-rep-original.zip
|-- cepni_2024_climate_change_exposure_and_cost_of_equity.pdf
+-- data_code \
    |-- 1976-2020-president.xlsx
    |-- 1_calculating cost of equity.do
    |-- 2_merging cost of equity data with balance sheet and climate risk exposure data.do
    |-- 3_merging with financial ratios.do
    |-- 4_merging with state headquarters data.do
    |-- 5_estimations.do
    |-- 6_endogeneity analysis.do
    |-- 7_robustness checks.do
    |-- 8_channel analysis.do
    |-- compustat-crsp.xlsx
    |-- damodaran_data.xlsx
    |-- esg score.xlsx
    |-- financial_ratios.dta
    |-- firmquarter_score_2021q4_version_2022_nov_22.xlsx
    |-- firm_adress.xlsx
    |-- firm_stock_price.dta
    |-- main_sample.dta
    |-- newscount-climatechange.xlsx
    |-- sp500-us1m.xlsx
    |-- state level abnormal temperature data.xlsx
    |-- state level emission data.xlsx
    +-- state level extreme weather events data.xlsx
```

# T3. Bao-2025-MS

- Bao, L., Huang, D., & Lin, C. (**2025**). Can Artificial Intelligence Improve Gender Equality Evidence from a Natural Experiment. **Management Science**. [Link](https://doi.org/10.1287/mnsc.2022.02787), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/2026-Spring/Bao-2024-MS.pdf), [PDF-wp](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/2026-Spring/Bao-2024-MS-wp.pdf), [Appendix](https://pubsonline.informs.org/doi/suppl/10.1287/mnsc.2022.02787/suppl_file/mnsc.2022.02787.sm1.pdf), [Google](<https://scholar.google.com/scholar?q=Can Artificial Intelligence Improve Gender Equality Evidence from a Natural Experiment>), [Replication](https://services.informs.org/dataset/download.php?doi=mnsc.2022.02787).
  - **简介**：该文研究的问题是：当教师队伍的性别结构与观念短期难改时，能否借助被设计为“性别中性”的 AI 教学，改善学习效果并缩小既有性别差距？作者利用一次疫情隔离触发的自然实验：2021年1月当地疫情反弹导致16/36名教师被隔离，机构以 AI 复盘替代部分人类教师，形成处理组与对照组，并追回冲击前后两个学期的训练数据(2月春节无训练)。结果显示，AI 训练显著提高胜率与落子质量，并减少错误、重大错误及错误幅度；同时，女生的进步更快，干预后约 5 个月性别差距明显收敛乃至被消除。
  - 方法：
    - 双重差分 (DID)、三重差分 (DDD)
    - 内生性应对：样本选择偏误、遗漏变量敏感性分析、纠偏多变量联合检验
    - 稳健性检验、异质性分析部分都做的非常细致
    - 因果识别论证思路严谨、复现文档结构清晰


# T4. Huang-2020-JF

- Huang, Y., Pagano, M., & Panizza, U. (2020). Local Crowding‐Out in China. The Journal of Finance, 75(6), 2855–2898. Portico. [Link](https://doi.org/10.1111/jofi.12966) (rep), [PDF](http://www.pushan.org.cn/Private/Files/6382770613883614602008936831.pdf), [Google](<https://scholar.google.com/scholar?q=Local Crowding‐Out in China. The Journal of Finance, 75(6), 2855–2898>). [-Appendix-](https://onlinelibrary.wiley.com/action/downloadSupplement?doi=10.1111%2Fjofi.12966&file=jofi12966-sup-0001-OnlineAppendix.pdf), [Replication](https://onlinelibrary.wiley.com/action/downloadSupplement?doi=10.1111%2Fjofi.12966&file=jofi12966-sup-0002-ReplicationCode.zip) 
- 2006—2013 年期间，中国地方政府债务通过收紧民营企业的融资约束，对民营企业投资产生了挤出效应，而国有企业的投资活动未受显著影响。本文基于专项构建的中国地方政府债务数据集验证了上述结论。研究发现，地方政府债务规模越高的城市，民营企业投资水平越低；且相较于与外地银行联系更为紧密或外部融资依赖度较低的民营企业，与外地银行距离更远、外部融资依赖度更高的民营企业，其投资规模受地方政府债务的挤压程度更为显著。此外，在地方政府债务高企的城市，民营企业投资行为对内部现金流的敏感性显著增强。


# T5. Crosignani-2026-JFE-Export-Control
- Crosignani, M., Han, L., Macchiavelli, M., & Silva, A. F. (2026). Securing technological leadership? The cost of export controls on firms. Journal of Financial Economics, 175, 104192. [Link](https://doi.org/10.1016/j.jfineco.2025.104192) (rep), [PDF](), [PDF-wp](http://matteocrosignani.com/site/wp-content/uploads/2025/04/CHMS_Tech_Leadership.pdf), [Google](<https://scholar.google.com/scholar?q=Securing technological leadership? The cost of export controls on firms>). [Replication](https://data.mendeley.com/datasets/sw4y26xcd4/2) 
  - R codes 为主；有一张表格是用 Stata 做的 (`c4_banklending.do`)
  - 技术难度不大，关键在于学习作者的论证思路和研究设计
    - DID 设计: 利用美国对中国出口管制政策的出台作为外生冲击，考察受影响的美国供应商和中国客户的市场反应和经营表现。
    - 事件研究法 (Event Study): Fig 5. `Cumulative abnormal returns on targeted Chinese firms`
  - **摘要**：为维护本国的技术领先地位，美国限制本土供应商向特定中国企业出口尖端技术。受此类出口管制政策影响，美国本土供应商虽如政策制定者预期般终止了对中国客户的销售业务，却难以在本土或政治同盟地区开拓新的替代客户资源。其结果是，这些本土供应商的市值大幅缩水，盈利能力、雇佣规模及银行信贷规模均出现下滑。反观中国企业，尽管需要付出相应成本，但其供应链重构行动更为积极主动。综上，出口管制政策反而给那些研发政策旨在保护的尖端技术的美国企业带来了更为沉重的成本负担。


![Crosignani-2026-JFE-Fig03](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/Crosignani-2026-JFE-Fig03.png)
> **Fig. 3. Cumulative abnormal returns around announcement dates**. This figure shows the cumulative abnormal returns (CAR) of affected suppliers in a [-10, 20] day window around the announcement date of the inclusion of a target entity in the BIS lists. Panel A shows CARs using the Fama-French 3-factor model (Fama and French, 1993) while Panel B uses the Fama-French 5-factor model (Fama and French, 2015). The dashed vertical line represents the day before announcement date. The solid red line represents the average CARs and the dot-dash blue lines represent the $95 \%$ confidence intervals. (For interpretation of the references to color in this figure legend, the reader is referred to the web version of this article.)

## 复现要求

- 复现正文中的主要结果，要使用 Stata 或 Python 来实现。(原作者的主要结果是使用 R 实现的)


## 复现文档说明

作者提供的是 Pseduo 数据和完整的代码文件，供读者复现论文中的主要结果。因此，代码都可以跑通，但未必能完全复现论文中的结果。 

复现文档的结构如下：

- C. List of codes

  - (1) c0_setup.R
  - (2) c1_Figure1_3.R
  - (3) c1_Figure2_summary.R
  - (4) c1_Figure2_us_suppliers_stack.R
  - (5) c2_Figure4_china_supply_chain.R
  - (6) c2_Other_suppliers.R
  - (7) c3_china_car_m3_m4.R
  - (8) c4_banklending.do

- D. Required software
  - R 4.4.5
  - Stata 18

- Stata commands
  - `levels`, 
  - `ppmlhdfe`: 用于估计 Poisson Pseudo-Maximum Likelihood (PPML) 模型，适用于处理大量零值的贸易流数据。 

# T6. Kilic-2026-JFE

- Kilic, M., & Tüzel, Ş. (2026). Investing in misallocation. Journal of Financial Economics, 176, 104208. [Link](https://doi.org/10.1016/j.jfineco.2025.104208) (rep), [PDF](https://doi.org/10.1016/j.jfineco.2025.104208), [Google](<https://scholar.google.com/scholar?q=Investing in misallocation>). [-Appendix-](https://ars.els-cdn.com/content/image/1-s2.0-S0304405X25002168-mmc1.pdf), [Replication](https://data.mendeley.com/datasets/vmhdthtzxg/1).
  - 本文研究发现，在标准普尔资本 IQ 数据库（Compustat）的样本企业中，有 20% 的企业尽管资本边际产出（MPK）处于中位数以下水平，却维持着高于中位数的投资率，这一现象看似构成了资源的 “错配”。进一步分析表明，这类企业普遍成立时间较短，且在后续年份中更有可能实现销售额与资本边际产出的大幅跃升。此类企业对创新活动贡献突出，其投资行为能够有效预测未来的总体生产率，所创造的价值超出了其当期资本边际产出所能衡量的范畴。本文构建并估计了一个简约的企业内生增长模型，该模型不仅能够刻画企业投资行为的核心横截面特征，还可支持反事实分析。研究显示，若在设定假想投资政策时忽略企业未来业绩跃升的潜在可能性，虽能缩小资本边际产出与投资率的离散程度，但同时也会导致总体生产率水平下降。
  - 作者提供了一份「伪数据」，用于演示论文中实证结果的实现过程
  - 也提供了 dofiles 来复现论文中的主要表格和图形
  
# T7. Baker-2026-JFE

- Baker, S. R., Bloom, N., Davis, S. J., & Kost, K. (2026). Policy news and stock market volatility. Journal of Financial Economics, 175, 104187. [Link](https://doi.org/10.1016/j.jfineco.2025.104187) (rep), [PDF-wp](https://static1.squarespace.com/static/5e2ea3a8097ed30c779bd707/t/673f8453a8f94f09d66b14d5/1732215892470/Policy+News+and+Stock+Market+Volatility%2C+19+November+2024.pdf), [Google](<https://scholar.google.com/scholar?q=Policy news and stock market volatility>). [Replication](https://data.mendeley.com/datasets/rmhtcwnvrk/1)
  - Stata codes
  - **摘要**： 本文以报纸文本为基础，构建了日度与月度双频率的**股票市场波动率（Equity Market Volatility, EMV）追踪指标**。研究发现，本文构建的核心EMV追踪指标，无论在样本内还是样本外，均与波动率指数（VIX）及标准普尔500指数收益率波动率保持高度联动。同时，本文借助报纸文本的篇幅占比，进一步构建了四十项分类EMV追踪指标。分析显示，大宗商品市场、利率、房地产市场、宏观经济总量以及通胀相关新闻，在EMV相关报道中占据主导地位。政策类新闻亦是引发市场波动的重要来源：30%的EMV相关报道涉及税收政策，30%围绕货币政策展开，另有25%提及各类监管政策。本文将报纸文本构建的EMV追踪指标，与上市公司10-K文件的文本分析结果相结合，得到了月度层面的企业异质性风险暴露指标。研究证实，即便在控制企业固定效应与时间固定效应后，该风险暴露指标仍能有效解释企业已实现波动率的横截面结构特征及其动态演变规律。


# T8. Carpenter-2026-JFE-中美债券收益风险
- Carpenter, J. N., Lu, F., & Whitelaw, R. F. (**2026**). Government bond risk and return in the US and China. **Journal of Financial Economics**, 176, 104224. [Link](https://doi.org/10.1016/j.jfineco.2025.104224) (rep), [PDF-wp](https://pages.stern.nyu.edu/~rwhitela/papers/Government%20Bond%20Risk%20and%20Return%20in%20the%20US%20and%20China.pdf), [Google](<https://scholar.google.com/scholar?q=Government bond risk and return in the US and China>). [Replication](https://data.mendeley.com/datasets/h4t3bpbrvn/2), 
  - Table 1 and Table 2: Python codes
  - Table 3-6, Stata 16

- 本文借鉴权益资产风险 - 收益领域的相关研究成果，提出一种全新的债券风险与风险溢价建模方法。该方法摒弃了传统模型为推导债券价格解析解而施加的严格约束条件。本文基于美国与中国两大市场，对债券主成分因子投资组合的波动率与夏普比率的联合动态特征展开参数估计，选取的预测变量涵盖收益率曲线相关指标，针对美国市场额外纳入波动率指数（VIX）。研究结果表明，利率风险的价格与数量之间存在复杂的时变关系，这一特征与现有文献的理论分析框架并不相符。而美国与中国市场之间呈现的显著差异，进一步印证了本文所提出的更具灵活性的建模方法具有应用必要性。


![](https://ars.els-cdn.com/content/image/1-s2.0-S0304405X25002326-gr1_lrg.jpg)

## 债券因子模型与波动率指标核心概念释义
1.  **债券主成分因子投资组合（Principal-component bond-factor portfolios）**
    指基于**主成分分析（PCA）** 提取债券收益率变动的核心驱动因子（如水平因子、斜率因子、曲率因子），并依据因子暴露度构建的投资组合。该方法可有效降维，捕捉债券市场的系统性风险，常用于债券收益归因与风险对冲。

2.  **波动率（Volatility）**
    衡量债券资产或投资组合价格/收益率的波动程度，反映资产的风险水平。在本文中特指**时变波动率**，即波动率随时间变化的动态特征，常用GARCH类模型或滚动窗口法进行估计。

3.  **夏普比率（Sharpe Ratio）**
    核心风险调整收益指标，计算公式为：
    $$\text{Sharpe Ratio}=\frac{R_p-R_f}{\sigma_p}$$
    其中 $R_p$ 为投资组合收益率，$R_f$ 为无风险收益率，$\sigma_p$ 为组合收益率的标准差。该指标越高，代表单位风险所获得的超额收益越高。

4.  **收益率曲线变量（Yield curve variables）**
    描述国债收益率曲线形态与位置的关键指标，常见的包括：
    - 水平因子：长期国债收益率的均值，反映整体利率水平；
    - 斜率因子：长期收益率与短期收益率的差值，反映期限利差；
    - 曲率因子：中期收益率与长、短期收益率的偏离程度。

5.  **波动率指数（VIX）**
    又称“恐慌指数”，通常以标普500指数期权价格为基础计算，反映市场对未来30天的预期波动率。在债券研究中，VIX常作为**投资者情绪与市场风险偏好**的代理变量，用于预测利率风险溢价。

6.  **利率风险的价格与数量（Price and quantity of interest rate risk）**
    - 利率风险的**数量**：指债券资产对利率变动的敏感程度，常用久期、凸性或因子暴露度衡量；
    - 利率风险的**价格**：指承担单位利率风险所获得的风险溢价，即风险因子的价格，是资产定价的核心参数。

7.  **解析解约束（Closed-form bond prices restrictions）**
    传统债券定价模型（如仿射期限结构模型）为推导债券价格的解析表达式，通常对利率动态过程、风险溢价形式施加严格的参数约束（如线性假设、正态分布假设）。本文提出的新方法则放松了此类约束，提升模型灵活性。

# T9. Hau-2024-JF

Hau, H., Huang, Y., Lin, C., Shan, H., Sheng, Z., & Wei, L. (2024). FinTech Credit and Entrepreneurial Growth. **The Journal of Finance**, 79(5), 3309–3359. Portico. [Link](https://doi.org/10.1111/jofi.13384) (rep), [PDF](http://sci-hub.ren/10.1111/jofi.13384), [-Appendix-](https://onlinelibrary.wiley.com/action/downloadSupplement?doi=10.1111%2Fjofi.13384&file=jofi13384-sup-0001-InternetAppendix.pdf), [Google](<https://scholar.google.com/scholar?q=FinTech Credit and Entrepreneurial Growth. The Journal of Finance, 79(5), 3309–3359>). [Replication](https://onlinelibrary.wiley.com/action/downloadSupplement?doi=10.1111%2Fjofi.13384&file=jofi13384-sup-0002-ReplicationCode.zip)
- 本文基于阿里巴巴线上零售平台为入驻商户提供的自动化信贷额度，以及信贷决策算法中存在的断点特征展开研究。结果表明，商户获得金融科技信贷支持后，其销售额增长率、交易额增长率均显著提升，且基于商品品质、服务质量及履约表现的客户满意度评分也随之提高。上述效应在信贷风险信息不对称程度更高、抵押品持有量更少的商户群体中表现尤为显著，这一特征凸显出金融科技信贷相较于传统信贷技术所具备的信息优势。
- 文中提供了简单的例子，可以采用模拟来演示

![Hau-2024-JF-Figure01-histogram-RDD](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/Hau-2024-JF-Figure01-histogram-RDD.png)

![Hau-2024-JF-Figure02-RDD](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/Hau-2024-JF-Figure02-RDD.png)


# T10. Yang-2024-EE

> 计数模型-多期DID应用

Yang, Z., & Ding, H. (2024). Turning a blind eye: How local government fiscal distress affects the entry of energy-intensive enterprises. **Energy Economics**, 138, 107828. [Link](https://doi.org/10.1016/j.eneco.2024.107828) (rep), [PDF](https://doi.org/10.1016/j.eneco.2024.107828), [Google](<https://scholar.google.com/scholar?q=Turning a blind eye: How local government fiscal distress affects the entry of energy-intensive enterprises>).
[Replication](https://ars.els-cdn.com/content/image/1-s2.0-S014098832400536X-mmc1.zip)

- **摘要**： 本文考察了地方财政困境对能源密集型创业企业的影响效应。研究基于环境规制视角，从理论层面构建了政府财政困境与能源密集型创业活动之间作用机制的分析框架。借助最新可得的企业注册数据，本文采用**泊松回归**模型展开实证检验，结果表明：由外生性税制改革引致的县级政府财政状况恶化，会显著推动能源密集型企业的新增设立。进一步研究发现，能源密集型企业进入规模的扩张，主要源于环境规制的放松，而非其他政策调整的驱动。对企业属性的分析显示，新增的能源密集型企业多为大型企业与民营企业。拓展性检验结果表明，产业集聚程度、区域市场化水平与法治环境，会对财政困境影响能源密集型企业设立的作用效果产生负向调节效应。本文的研究揭示了政府财政困境可能引发的潜在环境后果。

$$
\text { EnergyFirm }_{i t}=\exp \left(\sum_{t=2001, t \neq 2004}^{2007} \beta_t \cdot \text { Shock }_i \cdot \text { YrD }_t+\gamma^{\prime} \mathbf{X}_{i, t-1}+\lambda_{c t}+\mu_i\right) \varepsilon_{i t}
$$

- 方法：
  - `reghdfe`
  - `ppmlhdfe`
    - 左志勇, 2022, [Stata：三维引力模型介绍与估计-ppmlhdfe-nbreg-reghdfe](https://www.lianxh.cn/details/848.html).
  - `permute` 
  - `dpplot`
  - Placebo test


# T11. Mijit-2025-EE

>论文推介和复现：异质性多期DID-eventstudyinteract应用

Mijit, R., Hu, Q., Xu, J., & Ma, G. (2025). Greening through AI? The impact of Artificial Intelligence Innovation and Development Pilot Zones on green innovation in China. Energy Economics, 146, 108507. [Link](https://doi.org/10.1016/j.eneco.2025.108507) (rep), [PDF](http://sci-hub.ren/10.1016/j.eneco.2025.108507), [Google](<https://scholar.google.com/scholar?q=Greening through AI? The impact of Artificial Intelligence Innovation and Development Pilot Zones on green innovation in China>), [Replication](https://www.sciencedirect.com/science/article/pii/S0140988325003317#appSB) 

- 随着人工智能（AI）技术应用程度的不断提升，企业绿色创新水平有望实现显著跃升。本文以中国 A 股上市公司为研究样本，选取国家级人工智能创新发展试验区（AIIDPZ）政策的实施作为外生冲击，采用异质性稳健的渐进双重差分模型，实证评估了人工智能对企业绿色创新的影响效应。研究结果表明，人工智能创新发展试验区政策的落地，显著提升了辖区内企业绿色创新的数量与质量。进一步的异质性分析显示，该政策的影响存在明显差异：低污染企业更倾向于扩大绿色创新的数量规模，而资本密集型与劳动密集型行业则侧重于提升绿色创新的质量水平。机制检验结果揭示，人工智能创新发展试验区政策通过推动企业提高人工智能技术采纳程度，显著改善了企业运营效率，进而促进了绿色创新活动的提质升级。基于上述研究结论，本文建议持续推进人工智能技术与各产业的深度融合，尤其要依托人工智能驱动的效率红利，助力绿色发展战略的落地实施。


**方法**：异质性多期 DID 设计 + 事件研究法 (Event Study) 

- `eventstudyinteract`，[Sun](https://doi.org/10.1016/j.jeconom.2020.09.006) and Abraham ([2021](http://sci-hub.ren/10.1016/j.jeconom.2020.09.006))
  - Sun, L., & Abraham, S. (2021). Estimating dynamic treatment effects in event studies with heterogeneous treatment effects. Journal of Econometrics, 225(2), 175–199. [Link](https://doi.org/10.1016/j.jeconom.2020.09.006), [PDF](http://sci-hub.ren/10.1016/j.jeconom.2020.09.006), [PDF2](https://arxiv.org/pdf/1804.05785), [Google](<https://scholar.google.com/scholar?q=Estimating dynamic treatment effects in event studies with heterogeneous treatment effects>), [Slides](https://lsun20.github.io/event_studies_slides.pdf)
  - Stata 命令：
    - `eventstudyinteract`
    - `lincomest`


# T13. Leblebicioğlu-2025-AEJ-EP

- Leblebicioğlu, A., & Savaşer, T. (2025). The Not-So-Uniform Effects of Trade Secret Protection on Business Entry. **American Economic Journal**: Economic Policy, 17(4), 192–227. [Link](https://doi.org/10.1257/pol.20220814) (rep), [PDF](http://sci-hub.ren/10.1257/pol.20220814), [Appendix](https://www.aeaweb.org/doi/10.1257/pol.20220814.appx), [Google](<https://scholar.google.com/scholar?q=The Not-So-Uniform Effects of Trade Secret Protection on Business Entry>). [-Replication-](https://www.openicpsr.org/openicpsr/project/201465/version/V1/view) 
  - 加强商业秘密保护 (UTSA 实施) 会抑制小企业的创立和进入；但会促进大企业的进入。
  - 本文探讨了商业秘密保护制度对美国新企业创立活动的影响。研究发现，各州采纳《统一商业秘密法》（UTSA）以强化知识产权保护后，辖区内企业与营业机构的整体进入率呈下降态势。这一结果主要由初创企业与小型企业的营业机构进入率下滑所驱动；与之相对，该法案的实施显著提升了在位企业与大型企业的营业机构进入率。进一步分析表明，在知识产权与商业秘密依赖度更高的行业、以及外部融资依赖型行业中，《统一商业秘密法》对新企业创立的抑制效应表现得更为突出。

# T14. Stata 程序编写：Oster (2019) 系数稳定性检验的 Stata 实现

根据如下理论分析和 [github-`coefstability`](https://github.com/gratzt/Coef-Stability-Oster) 中的初始代码编写一个正式的 Stata 程序 `coefstability.ado`，用于实现 Oster (2019) 提出的系数稳定性检验方法。

- 连老师会提供全程指导
- 完成后的论文可以合作投稿到 Stata Journal

> Oster, E. (**2019**). Unobservable Selection and Coefficient Stability: Theory and Evidence. **Journal of Business & Economic Statistics**, 37(2), 187–204. [Link](https://doi.org/10.1080/07350015.2016.1227711), [PDF](http://sci-hub.ren/10.1080/07350015.2016.1227711), [Google](<https://scholar.google.com/scholar?q=Unobservable Selection and Coefficient Stability: Theory and Evidence>). [-cited-5000次](https://scholar.google.com/scholar?cites=11936978270607540916&as_sdt=2005&sciodt=0,5&hl=zh-CN), [github-`coefstability`](https://github.com/gratzt/Coef-Stability-Oster)

相关应用：
- Acheampong, A. O., & Said, R. (2024). Financial inclusion and the global net-zero emissions agenda: Does governance quality matter? Energy Economics, 137, 107785. [Link](https://doi.org/10.1016/j.eneco.2024.107785) (rep), [PDF](http://sci-hub.ren/10.1016/j.eneco.2024.107785), [Google](<https://scholar.google.com/scholar?q=Financial inclusion and the global net-zero emissions agenda: Does governance quality matter>). [Replication](https://ars.els-cdn.com/content/image/1-s2.0-S0140988324004936-mmc1.zip) 
  - 存放于 `PX_papers4/Acheampong-2024-EE-Oster-2019-omit-variable-test` 目录下
  
```stata
//Table 10: Oster (2019) test for omitted variable bias
//OLS results and Oster stability test
eststo clear
eststo: regress lnco2kt  lnrgdpc lnrgdpc2 lnrenew lnfdi  lntrad lnurb FI i.year,  robust
psacalc delta FI, rmax (1)
```

- Cepni, O., Şensoy, A., & Yılmaz, M. H. (2024). Climate change exposure and cost of equity. Energy Economics, 130, 107288. [Link](https://doi.org/10.1016/j.eneco.2023.107288) (rep), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/2026-Spring/Cepni_2024_Climate_change_exposure_and_cost_of_equity.pdf), [Google](<https://scholar.google.com/scholar?q=Climate change exposure and cost of equity>). [Replication](https://ars.els-cdn.com/content/image/1-s2.0-S0140988323007867-mmc1.zip)
  - 存放于 `PX_papers4/Cepni-2024-EE-xtabond2-DID-robust` 目录下
- Bao, L., Huang, D., & Lin, C. (2024). Can Artificial Intelligence Improve Gender Equality? Evidence from a Natural Experiment. Management Science. [Link](https://doi.org/10.1287/mnsc.2022.02787), [PDF](https://papers.ssrn.com/sol3/Delivery.cfm/4202239.pdf?abstractid=4202239&mirid=1), [Google](<https://scholar.google.com/scholar?q=Can Artificial Intelligence Improve Gender Equality? Evidence from a Natural Experiment>).

```stata
*- table_b1.do

// =======
// Table B1: Oster (2019)
// =======

** set path **
local path_data "$root/Data/"
local path_results "$root/Results/"

use "`path_data'/data_main.dta", clear

* install psacalc
ssc install psacalc

* pca
pca visual_positive visual_negative vocal_positive vocal_negative verbal
predict pc1 pc2 pc3, score

areg quality pc2 teacher_gender teacher_age teacher_experience age study gender, absorb(month)


** Part 1: min(2R^2,1)

bs r(beta), rep(100): psacalc beta pc2, rmax(0.40) delta(1) model(areg quality pc2 teacher_gender teacher_age teacher_experience age study gender, absorb(month))

bs r(beta), rep(100): psacalc beta pc2, rmax(0.40) delta(1.5) model(areg quality pc2 teacher_gender teacher_age teacher_experience age study gender, absorb(month))

psacalc delta pc2, rmax(0.40) beta(0) model(areg quality pc2 teacher_gender teacher_age teacher_experience age study gender, absorb(month))
```

# T15. Manso-2025-JFE

> 家庭债务积压与人力资本投资

- Manso, G., Rivera, A., Wang, H. (Grace), & Xia, H. Household debt overhang and human capital investment, Journal of Financial Economics,
172, 2025, 104141. [Link](https://doi.org/10.1016/j.jfineco.2025.104141) (rep), [PDF](http://sci-hub.ren/10.1016/j.jfineco.2025.104141), [Google](<https://scholar.google.com/scholar?q=>). [Replication](https://data.mendeley.com/datasets/vnbyftyjzn/1)
  - 存放于：[Manso-2026-JFE-Family-debt-overhang]
- **摘要：** 与劳动收入不同，人力资本具有人身依附性，无法完全让渡给债权人。因此，相较于劳动供给，人力资本投资受**债务积压**（debt overhang）问题的冲击更具韧性。本文构建一个动态模型以阐释二者间的差异，研究发现：家庭债务水平对劳动供给与人力资本投资的影响均呈倒U型特征，但随着债务规模扩大，人力资本投资的下降幅度显著更小。值得注意的是，人力资本的价值需以家庭的劳动供给意愿为前提，债务积压引致的劳动供给大幅收缩，会反向抑制家庭的事前人力资本投资行为。本文为该理论模型提供了相应的经验证据支持。
- **关键词**：家庭债务；人力资本投资；劳动技能获取；债务积压；家庭违约

# T16. Blonz-2026-JFE

- Blonz, J., Roth Tran, B., & Troland, E. (2026). The canary in the coal decline: Appalachian household finance and the transition from fossil fuels. Journal of Financial Economics, 175, 104167. [Link](https://doi.org/10.1016/j.jfineco.2025.104167) (rep), [PDF](http://sci-hub.ren/10.1016/j.jfineco.2025.104167), [Google](<https://scholar.google.com/scholar?q=The canary in the coal decline: Appalachian household finance and the transition from fossil fuels>). [Replication](https://data.mendeley.com/datasets/33t88r4jrk/1) (1.1G)

- **摘要：** 本文基于个人层面信贷数据，考察了 2011—2018 年阿巴拉契亚地区煤炭开采业的衰退对当地家庭财务状况产生的影响。本文利用电力行业煤炭需求的外生变动作为研究切入点，研究发现，煤炭需求下滑会在冲击发生后的两年内导致居民信贷评分下降，并加剧其财务困境。值得注意的是，上述影响无法单纯由煤矿工人家庭的失业问题解释。进一步分析表明，年龄较大群体与中低信贷评分群体的信贷评分降幅最大，且面临的财务困境最为严重。本文结论表明，能源结构向非化石燃料转型的过程，或会给其他化石燃料开采社区带来显著的经济成本。


# T17. Alertus-2025-JFE

- Albertus, J. F., Glover, B., & Levine, O. (2025). The real and financial effects of internal liquidity: Evidence from the Tax Cuts and Jobs Act. Journal of Financial Economics, 166, 104006. [Link](https://doi.org/10.1016/j.jfineco.2025.104006) (rep), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/FinE-2025/Albertus_2025_The_real_and_financial_effects_of_internal_liquidity_Evidence_from_the_Tax_Cuts_and_Jobs_Act.pdf), [Google](<https://scholar.google.com/scholar?q=The real and financial effects of internal liquidity: Evidence from the Tax Cuts and Jobs Act>). [-Appendix-](https://ars.els-cdn.com/content/image/1-s2.0-S0304405X25000145-mmc1.pdf), [Replication](https://data.mendeley.com/datasets/tn6hvjsb67/1), [-cited-](https://scholar.google.com/scholar?cites=9887157776117305379&as_sdt=2005&sciodt=0,5&hl=zh-CN).
  - 方法：交乘项，三个交乘项
  - 分析框架很好
  - 《减税与就业法案》帮助美国跨国企业释放了高达 1.7 万亿美元的海外留存现金。本文考察了企业应对此次流动性冲击的实体层面与财务层面反应，研究发现：无论企业面临的融资约束程度如何，其资本支出、雇佣规模、研发投入以及并购活动均未出现增长。在财务决策方面，企业仅将新增流动性的约三分之一用于股东分红，另有半数资金以现金形式留存。值得注意的是，这种高额现金留存行为与公司治理水平低下并无关联。即便是治理机制完善且融资约束较小的企业，依然倾向于将此次流动性冲击带来的资金以现金形式持有，这一现象难以用现有理论进行合理解释。

# T18. Yu-2025-JFE-Bank-CEOs

> 该文最早的 working paper 版本发表于 2018 年，经过多次修改后于 2025 年发表在 JFE 上。
> - 该文的复现资料仅包含作者处理后的最终数据。
> - 作者通过了原始数据清理过程的 dofile，但没有提供中间数据文件。

- Yu, G. Y. (2025). Do bank CEOs learn from banking crises? Journal of Financial Economics, 166, 104009. [Link](https://doi.org/10.1016/j.jfineco.2025.104009) (rep), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/FinE-2025/Yu_2025_JFE_Do_bank_CEOs_learn_from_banking_crises.pdf), [PDF-wp](https://ink.library.smu.edu.sg/cgi/viewcontent.cgi?params=/context/lkcsb_research/article/8683/&path_info=DoBankCEOs_LearnCrisis_sv.pdf), [Google](<https://scholar.google.com/scholar?q=Do bank CEOs learn from banking crises>), [-Appendix-](https://ars.els-cdn.com/content/image/1-s2.0-S0304405X25000170-mmc1.pdf), [Replication](https://data.mendeley.com/datasets/frp6x7xck3/1).
  - R Program Code: The graph.R file, located in the /code folder, generates Figure 1 and Figure 2 as reported in the manuscript.
  - 其它表格和图形使用 Stata 完成。 
  - [replication/code] 文件夹中的 `01_data_clean_Yu_2025_JFE.do` 和 `02_regression_Yu_2025_JFE.do` 文件是我拆分后的文件，分别用于数据清理和回归分析。
    - 仅适用 `02_regression_Yu_2025_JFE.do` 文件即可复现论文中的主要结果，因为数据清理过程需要原始数据文件，而作者并未提供这些文件。
  - **摘要：** 银行首席执行官（CEO）在职业生涯早期经历的 20 世纪 80 年代储贷危机，是否会影响其后续管理银行的经营表现？本文以储贷危机期间 CEO 任职所在州的银行倒闭率作为危机暴露程度的衡量指标，研究发现：危机暴露程度更高的 CEO 所管理的银行，风险承担水平更低，且在 2008 年金融危机中表现出更强的生存能力。具体而言，这些 CEO 针对储贷危机的诱因领域调整了风险态度 —— 更为深刻的危机经历降低了银行的利率风险、高风险金融创新敞口以及信贷风险。为确立研究结论的因果解释，本文通过评估 CEO 籍贯所在州的危机暴露影响，并利用 CEO 退休引致的准外生人事变动展开分析。综上，CEO 从过往行业危机中汲取的经验，有助于降低其任职机构的风险敞口，并提升该机构在后续危机中的应对能力。


## 复现要求

- 在作者提供的 `02_regression_Yu_2025_JFE.do` 文件中，表格都输出为 `.tex` 格式，请修改这些代码，以便将回归结果输出为 `.docx` 或 `.xlsx` 格式，方便阅读。
- 请将所有统计和回归分析的结果表格、图形统一输出到 `replication/out` 文件夹中。


# T19. Duchin-2024-JF

- Duchin, R., Gao, J., & Xu, Q. (2024). Sustainability or Greenwashing: Evidence from the Asset Market for Industrial Pollution. **The Journal of Finance**, 80(2), 699–754. Portico. [Link](https://doi.org/10.1111/jofi.13412) (rep), [PDF](https://file-lianxh.oss-cn-shenzhen.aliyuncs.com/Refs/cRefs/Duchin_2024_JF_Sustainability_or_Greenwashing.pdf), [Google](<https://scholar.google.com/scholar?q=Sustainability or Greenwashing: Evidence from the Asset Market for Industrial Pollution.>). [-Appendix-](https://onlinelibrary.wiley.com/action/downloadSupplement?doi=10.1111%2Fjofi.13412&file=jofi13412-sup-0001-InternetAppendix.pdf), [Replication](https://onlinelibrary.wiley.com/action/downloadSupplement?doi=10.1111%2Fjofi.13412&file=jofi13412-sup-0002-ReplicationCode.zip) (195M).
- 方法：
  - 多期 DID
  - `mlogit`: Multi-logit choice model 
  - `margin`: 用于计算和解释回归模型中的边际效应
  - `reghdfe`: 高维固定效应回归模型，多期 DID 分析
  - `ppmlhdfe`: Poisson Pseudo-Maximum Likelihood (PPML) 模型
  - `winsor2`: 缩尾处理
  - `esttab`, `estto`, `estadd`: 回归结果输出
  - Event Study
- **摘要**：本文对污染型工厂的资产交易市场展开研究。研究发现，企业会迫于环境压力剥离旗下污染型工厂，而收购方多为环境压力较小、且与出售方存在供应链关系或合资合作的企业。值得注意的是，资产剥离行为并未降低整体污染水平，但出售方在后续的业绩说明会上会着重宣传其可持续发展策略；且剥离的污染型工厂越多，出售方获得的收益越高，同时还能实现环境、社会及治理（ESG）评级提升与合规成本下降。综上，污染型工厂的资产交易市场使企业得以重塑自身业务边界，打造出践行环保理念的外部形象，此过程虽未对污染产生实质性改善，却为交易双方创造了显著的贸易收益。

# T20. Hansen-2025-JAE-DID中的jackknife标准误

文中展示了 4 篇经典的 DID 论文中的标准误计算方法，并与 jackknife 标准误进行对比分析，发现经典论文中的标准误计算方法在某些情况下可能存在低估的风险。

Hansen, B. E. (2025). Standard Errors for Difference‐in‐Difference Regression. Journal of Applied Econometrics, 40(3), 291–309. Portico. [Link](https://doi.org/10.1002/jae.3110) (rep), [PDF](https://users.ssc.wisc.edu/~behansen/papers/jae_25.pdf), [PDF2](https://onlinelibrary.wiley.com/doi/epdf/10.1002/jae.3110), [Google](<https://scholar.google.com/scholar?q=Standard Errors for Difference‐in‐Difference Regression. Journal of Applied Econometrics, 40(3), 291–309>).[Replication](https://journaldata.zbw.eu/dataset/standard-errors-for-difference-in-difference-regression), [Replication-作者主页版](https://users.ssc.wisc.edu/~behansen/progs/jae_25.html), 

- **摘要**： 本文论证了**刀切法（jackknife methods）** 在双重差分（Difference-in-Difference, DID）回归模型的标准误、p值及置信区间构建中的适用性。本文系统梳理了聚类稳健法、自助法与刀切法三类标准误估计方法，研究表明，在常规研究场景下，传统估计方法的表现存在显著不足。相比之下，本文提出的刀切法推断方法在广泛情境中均具备良好适用性。为进一步佐证该方法的实践价值，本文对多项具有影响力的双重差分应用研究进行了重复检验，结果显示，采用刀切法进行标准误计算与统计推断时，研究结论的统计推断结果可能发生实质性改变。
- Stata 官网介绍：[Robust inference for linear models](https://www.stata.com/features/overview/robust-inference-for-linear-models/)


# T21. Christensen-2025-JFE-Monte-Carlo-Simulation ？

- **任务：** 做附录 B 中的蒙特卡洛模拟分析。
  - 无需复现全文，只需要做附录 B 中的蒙特卡洛模拟分析即可。
  - 不过，需要借助 AI 简要介绍一下论文的背景和主要结论，然后把重点转移到附录 B 的蒙特卡洛模拟分析上来。如果对布朗运动和跳跃扩散模型不熟悉，可以查阅相关资料进行学习，也可以和我联系，我可以提供一些参考资料。
- Note: 这篇论文的背景有些过于复杂，有些挑战。不过对于想从事金融经济学实证研究的同学来说，理解这篇论文的背景和方法是非常有益的。

- Christensen, K., Timmermann, A., & Veliyev, B. (2025). Warp speed price moves: Jumps after earnings announcements. Journal of Financial Economics, 167, 104010. [Link](https://doi.org/10.1016/j.jfineco.2025.104010) (rep), [PDF](http://sci-hub.ren/10.1016/j.jfineco.2025.104010), [Google](<https://scholar.google.com/scholar?q=Warp speed price moves: Jumps after earnings announcements>). [-Appendix-](https://ars.els-cdn.com/content/image/1-s2.0-S0304405X25000182-mmc1.pdf), [Replication-Matlab code](https://data.mendeley.com/datasets/925crksynw/2).
  - **摘要**： 我们研究了财报发布后股票价格的跳跃行为。利用高频数据，我们发现财报发布引发的价格跳跃具有显著的时间聚集特征，且这些跳跃在发布后的前几分钟内尤为频繁。我们提出了一种基于布朗运动与跳跃扩散模型相结合的理论框架，以解释这一现象。通过蒙特卡洛模拟，我们展示了该模型在捕捉财报发布后价格跳跃动态方面的有效性。我们的研究结果不仅丰富了对市场微观结构的理解，也为投资者在财报季节制定交易策略提供了实证依据。

# T22. Chen-2025-JFE-环境规制与资产重组

- Chen, J. (2025). Redeploying dirty assets: The impact of environmental. **Journal of Financial Economics**, 170, 104070. [Link](https://doi.org/10.1016/j.jfineco.2025.104070) (rep), [PDF](http://sci-hub.ren/10.1016/j.jfineco.2025.104070), [Google](<https://scholar.google.com/scholar?q=Redeploying dirty assets: The impact of environmental>). [Replication](https://data.mendeley.com/datasets/4tmgrrgmyz/2) (900M)
  - DID with multiple time periods
  - **摘要**：本文考察了企业剥离污染资产的能力对其污染动机的影响。本文选取一项**免除收购方既往污染责任的重大改革**作为实证场景，基于双重差分模型的分析结果表明，该改革不仅降低了企业有毒污染物排放量，还缓解了企业破产风险并提升了企业价值。分组检验结果显示，污染物排放的下降效应主要由财务状况较差、资产规模较小的企业驱动。上述研究结论揭示了一条新颖的**净资产传导渠道**：通过限制事后污染责任，该改革提升了资产持有方的事前净资产水平，进而削弱了其从事过度排污等高风险行为的动机。
