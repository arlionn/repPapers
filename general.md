

## IV 

- Andrews, I., Stock, J. H., & Sun, L. (2019). Weak Instruments in Instrumental Variables Regression: Theory and Practice. Annual Review of Economics, 11(1), 727–753. [Link](https://doi.org/10.1146/annurev-economics-080218-025643), [PDF](https://www.annualreviews.org/docserver/fulltext/economics/11/1/annurev-economics-080218-025643.pdf?expires=1766962031&id=id&accname=guest&checksum=499938A58C701FB832238ED312FDF263), [Google](<https://scholar.google.com/scholar?q=Weak Instruments in Instrumental Variables Regression: Theory and Practice>). 
- Keane, M. P., & Neal, T. (2024). A Practical Guide to Weak Instruments. Annual Review of Economics, 16(1), 185–212. [Link](https://doi.org/10.1146/annurev-economics-092123-111021), [PDF](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#), [Google](<https://scholar.google.com/scholar?q=A Practical Guide to Weak Instruments>).

### 8.  A SIMPLE GUIDE FOR APPLIED RESEARCHERS

Here we present a simple guide for applied researchers seeking to implement IV inference while avoiding the problems with the 2SLS t\-test. In the single instrument case we show how to use the AR test, and in the multiple instrument case we show how to use CLR. Given its widespread use among applied economists, we present Stata code to implement our suggestions. When we examined AER papers from 2011 to 2023, we found only 3 out of 52 that met our search criteria, used public data, and used software other than Stata. ^25^

First, consider the case in which outcome y is regressed on the single endogenous variable x and an exogenous control variable c, and where z is the excluded instrument. We suggest reporting results from the following procedures.

1. Run and report OLS. It is important to compare 2SLS and OLS results.
       In Stata: reg y x c, vce( type )
2. Run the first-stage regression of x on z and c.
       In Stata: reg x z c, vce( type )
3. Obtain a heteroskedasticity/cluster-robust F statistic for significance of the instrument.
       In Stata: test z = 0
4. Compute  ![](https://www.annualreviews.org/docserver/ahah/fulltext/economics/16/1/eq-111021-266.gif).
       In Stata: predict xhat, xb
5.  5.  Run the second-stage regression of y on  ![](https://www.annualreviews.org/docserver/ahah/fulltext/economics/16/1/eq-111021-267.gif)and use the t\-test from this regression to test H 0:β = 0. This t\-stat is the AR test of H 0:β = 0 in the one instrument case.
       In Stata: reg y xhat c, vce( type )
6.  6.  Construct a valid confidence interval by inverting the AR test.
       In Stata: weakiv ivregress 2sls y (x = z) c, vce( type )

In all these commands the "vce" option determines how the variance matrix of the parameter estimates is calculated. The results are rendered robust to heteroskedasticity or clustering via the option one specifies for "type," which refers to the data type---for example, vce(cluster personid) for panel data. Enter help reg in Stata for a list of options.

In step 3 it is important to use a robust F statistic, as recent papers by [Andrews et al. (2019)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B4) and [Young (2022)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B38) emphasize that 2SLS can suffer from low power and size distortions in environments with heteroskedastic and/or clustered errors, even if conventional F tests appear acceptable. As we showed in Section 6, if first-stage sample F is below roughly 50, one may be concerned that the 2SLS estimate may be no more reliable than OLS.

In step 5, the t\-statistic and p\-value from the second stage regression give the AR test of H 0:β = 0. The F version of the AR test is the square of the t\-statistic from the second-stage regression. ^26^ Always remember that the standard error from the-second stage regression is not valid for forming confidence intervals. Instead, the AR test should be inverted as in step 6, using the Stata command weakiv by [Finlay et al. (2013)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B13). ^27^

In step 6, if the confidence interval reported by weakiv is unbounded---i.e., it covers the entire grid---it means you do not have at least 95% confidence that the model is identified. This will happen if first-stage F is less than 3.84. You should not be doing IV in this case!

Importantly, our results suggest that the above methodology is preferred for all first-stage F statistics, not simply ones that are currently considered in the literature to be weak. As the strength of the instrument grows, inferences using the AR test and the t\-test converge.

Finally, we note that the popular user command ivreg2 in Stata also contains the AR test statistic, but we do not recommend it for two reasons. First, it does not (at the time of writing) report AR confidence intervals. Second, it reports 2SLS t\-test results that we argue are better left unknown, as this may lead to researchers trying to screen on specifications that contain a significant t\-test. This is undesirable for reasons shown in [Figure 7](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#f7) .

Next we consider the case of multiple instruments. In this case, we strongly advise against using 2SLS or the two-step GMM estimator (GMM-2S), which extends 2SLS to heteroskedastic data, as both suffer from severe bias toward OLS. Furthermore, the associated t\-tests suffer from severe size inflation and power asymmetry.

As we show elsewhere ([Keane & Neal 2023](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B18)), given homoskedasticity, the limited information maximum likelihood (LIML) estimator and associated CLR test largely avoid these problems. Continuously updated GMM, often called CUE, generalizes LIML to heteroskedastic data, while [Kleibergen (2005)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B20) provides a generalization of CLR. We recommend using these procedures in the overidentified case. ^28^ For concreteness, consider a case with two instruments z1 and z2. Then follow the procedure below.

1.  1.  Run and report OLS. It is important to compare 2SLS and OLS results.
       In Stata: reg y x c, vce( type )
2.  2.  Run the CUE estimator. ^29^ The  ![](https://www.annualreviews.org/docserver/ahah/fulltext/economics/16/1/eq-111021-268.gif)is only used to obtain the estimate of β. The CUE standard error and t\-stat should not be used for inference.
       In Stata: ivreg2 y (x = z1 z2) c, cue type
3.  3.  For inference obtain [Kleibergen's (2005)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B20) extension of CLR for GMM.
       In Stata: Run weakiv after step 2. The Kleibergen test of H 0:β = 0 will simply
       be called CLR. ^30^ A 95% confidence interval is also provided by default. ^31^
4.  4.  Obtain [Hansen's (1982)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B14) J-test. If it rejects the overidentifying restrictions, there is evidence the instruments are invalid so the results should not be trusted.
       In Stata: The J-test is provided in the ivreg2 results (see step 2).
5.  5.  Obtain and report [Olea & Pflueger's (2013)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B29) first-stage F statistic.
       In Stata: Run weakivtest after step 2. ^32^

There are some published papers that use 2SLS and the t\-test but then report CLR as a robustness check. However, we advise against this procedure. First, it leads to the same type of problems we explained in [Figure 7](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#f7) . Second, CLR is designed for use with LIML or CUE, and, as we explain elsewhere ([Keane & Neal 2023](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B18), figure 10), mixing and matching estimators and test statistics based on different estimators can generate odd results.

We use [Olea & Pflueger's (2013)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B29) first-stage F statistic (O-F) because, as [Andrews et al. (2019)](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#right-ref-B4) note, it is inappropriate to use either a conventional or an heteroskedasticity-robust F to gauge instrument strength in nonhomoskedastic overidentified settings. ^33^

Lastly, it is worth noting that the CLR test is optimal in the overidentified case with homoskedastic errors. However, the theory literature has not settled on an optimal test for the heteroskedastic case. Therefore, there are some proposed alternatives to the Kleibergen test that we discuss in [Supplemental Appendix I](https://www.annualreviews.org/content/journals/10.1146/annurev-economics-092123-111021#supplementary_data) . In our experience these tests give similar results unless the data are poorly behaved (e.g., clustered data with few clusters).

## SDID-引力模型

- Nagengast, A. J., & Yotov, Y. V. (2025). Staggered Difference-in-Differences in Gravity Settings: Revisiting the Effects of Trade Agreements. American Economic Journal: Applied Economics, 17(1), 271–296. [Link](https://doi.org/10.1257/app.20230089) (rep), [PDF](http://sci-hub.ren/10.1257/app.20230089), [Appendix](https://www.aeaweb.org/doi/10.1257/app.20230089.appx), [Google](<https://scholar.google.com/scholar?q=Staggered Difference-in-Differences in Gravity Settings: Revisiting the Effects of Trade Agreements>). [Replication](https://doi.org/10.3886/E194561V1) (Stata codes)