
## 简介

这个页面记录了 Jounral of Applied Econometrics 近期发表的一些数据集和代码库的连接，供学习和参考。

## 控制变量-bad controls

- Clist, Paul (2025): The Common Problem of Bad Controls in Tests of the Linguistic Savings Hypothesis (Replication File). Version: 1.0. JCRE. Dataset. https://doi.org/10.15456/j1.2025224.1531306214


## IV
- Depalo, Domenico (2025): Your Season of Birth Tells Much of You and Your Background: European Edition (replication data). Version: 1.0. Journal of Applied Econometrics. Dataset. https://doi.org/10.15456/jae.2025276.0618710195
  - I adapt the approach in Buckles and Hungerman (2013) to show that in several European Union (EU) countries, between 2004 and 2020, the characteristics of the mothers giving birth in different quarters are significantly different. An implication of this finding is that quarter of birth is not a valid instrument in several applications where it has been used, e.g. return to education, even within the EU context. Beyond standard methods, partial identification techniques may help address this limitation.

## 时间序列和预测

- Baumeister, Christiane; Huber, Florian; Lee, Thomas K; Ravazzolo, Francesco (2025): Forecasting Natural Gas Prices in Real Time (replication data). Version: 1.0. Journal of Applied Econometrics. Dataset. https://doi.org/10.15456/jae.2025266.1900967125
  - Tags: expert fore-... natural gas ... out-of-sampl... real-time da... temperature ...

## 机器学习
- Fitzgerald Sice, Jack; Lattimore, Finn; Robinson, Tim; Zhu, Anna (2026): Double LASSO: Replication and Practical Insights (replication data). Version: 1.0. Journal of Applied Econometrics. Dataset. https://doi.org/10.15456/jae.2025335.0258270663
  - The rise of machine learning is one of the most prominent developments in applied econometrics in the past decade. The focus of much economic analysis is causal, rather than prediction, and Belloni, Chernozhukov & Hansen (2014) demonstrates how machine learning methods can be used in causal inference. This paper undertakes a narrow and wide replication of the Monte Carlo and empirical examples presented by Belloni et al. (2014). We discuss practical implications of this replication for the use of double machine learning methods in applied econometric research.

## Bunching

- Aronsson, T., Jenderny, K., Lanot, G. (2024). A maximum likelihood bunching estimator of the elasticity of taxable income. Journal of Applied Econometrics, 39(1). doi: 10.1002/jae.3015, [Replication](https://doi.org/10.15456/jae.2023262.1423597944) (Stata codes)
  - This paper develops a maximum likelihood (ML) bunching estimator of the elasticity of taxable income (ETI). Our structural approach provides a natural framework to simultaneously account for unobserved preference heterogeneity and optimization errors, and for measuring their relative importance. We characterize the conditions under which the parameters of the model are identified, and show that the ML estimator performs well in terms of bias and precision. The paper also contains an empirical application using Swedish data, showing that both the ETI and the standard deviation of the optimization friction are precisely estimated, albeit relatively small.


## 复现类论文

- Nunn & Wantchekon (2011) detect a long-lasting impact of the slave trade on current trust levels across
ethnic groups in Africa. They use data from Afrobarometer’s wave 3 to construct trust measures. While I
can perfectly replicate the original OLS and 2SLS findings in this wave starting from the same raw data,
using data from more recent waves which were collected after the paper was published, I fail to replicate
some of the paper’s central findings. Plausible explanations are discussed