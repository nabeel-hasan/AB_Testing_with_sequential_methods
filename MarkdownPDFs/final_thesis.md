
**Introduction**

The rapid growth of digital platforms, e-commerce, online advertising, and web-based applications has significantly increased the importance of data-driven decision-making in modern businesses. Organizations continuously introduce changes to their digital products and services to improve user engagement, customer experience, conversion rates, and overall business performance. However, determining whether a particular modification actually improves performance requires reliable statistical evaluation. Online controlled experiments, commonly known as A/B testing, have therefore become an important tool for evaluating the effectiveness of changes in digital environments (Kohavi, Tang, & Xu, 2020; Larsen et al., 2024)

A/B testing is a randomized experimental methodology in which users or impressions are divided into two groups: a control group (Version A) and a treatment group (Version B). The control group is exposed to the existing version of a digital product, whereas the treatment group receives a modified version. The performance of both groups is subsequently compared using predefined performance metrics to determine whether the introduced modification produces a statistically significant effect.

One commonly used metric in digital experimentation is the Click-Through Rate (CTR), which measures the proportion of impressions that generate clicks. CTR is particularly relevant in online advertising, search engines, email marketing, and website optimization because it provides a quantitative measure of user interaction with digital content.

The Click-Through Rate is mathematically expressed as:

$$
CTR=\frac{\text{Total Number of Clicks}}
{\text{Total Number of Impressions}}
$$

Since each impression produces one of two possible outcomes, either a click or a non-click, CTR can be modelled using a Bernoulli probability distribution. Consequently, the total number of clicks observed across a given number of impressions follows a binomial distribution. This provides an appropriate statistical foundation for comparing the CTRs of two experimental variants.

Traditional A/B testing generally follows a fixed-horizon or fixed-sample-size approach. Under this methodology, the required sample size is determined before the experiment begins using predefined statistical parameters, such as the significance level, statistical power, baseline CTR, and minimum detectable effect.

Once the predetermined sample size has been collected, a statistical hypothesis test is conducted to determine whether a significant difference exists between the control and treatment groups.

The conventional approach provides a well-established framework for controlling Type I and Type II errors. However, it also requires the experiment to reach its predetermined sample size before the final statistical decision can be made. In high-volume digital environments, where impressions and clicks are generated continuously, this requirement may increase experimentation time and delay business decisions (Kohavi et al., 2020)

An alternative approach is Sequential Testing, in which statistical evidence is evaluated repeatedly as new observations become available. Instead of waiting until the completion of a predetermined sample size, sequential methods allow researchers to monitor accumulating evidence and make decisions when predefined statistical conditions are satisfied.

One of the foundational methods of sequential hypothesis testing is the Sequential Probability Ratio Test (SPRT), introduced by Abraham Wald (1945). SPRT evaluates the likelihood of observed data under competing statistical hypotheses and determines whether sufficient evidence exists to accept one hypothesis or whether additional observations are required

The main motivation behind sequential testing is to improve the efficiency of statistical experimentation by potentially reducing the number of observations required to reach a decision while maintaining specified error probabilities.

<div style="page-break-after: always;"></div>

### **Fixed Horizon A/B Testing** 

**Fixed Sample Size A/B Testing for Comparing Two Click-Through Rates (CTR)**

Fixed Sample Size A/B Testing is a statistical experimentation approach used to compare the performance of two alternative versions of a digital product, webpage, advertisement, or application. The primary objective is to determine whether a modification introduced in the treatment version produces a statistically significant difference in performance compared with the existing version.

In this study, the performance of the two experimental groups is evaluated using the Click-Through Rate (CTR). CTR measures the proportion of impressions that result in clicks and is commonly used as a performance indicator in digital marketing and online experimentation.

The experiment consists of two independent groups:
- Group A (Control): Represents the existing version of the digital content.
- Group B (Treatment): Represents the modified version of the digital content.
The experiment follows a fixed sample size approach, in which the required number of impressions for both groups is determined before the experiment begins. Statistical inference is performed only after the predetermined sample size has been collected.

Click-Through Rate is defined as the ratio of the total number of clicks to the total number of impressions received by a particular version.

Let the following notations be defined:

For Group A (Control):

- $n_A$: Total number of impressions.
- $X_A$: Number of clicks.
- $p_A$: True population CTR of Group A.
- $\hat p_A$: Observed sample CTR of Group A.

For Group B (Treatment):

- $n_B$: Total number of impressions.
- $X_B$: Number of clicks.
- $p_B$: True population CTR of Group B.
- $\hat p_B$: Observed sample CTR of Group B.

The sample CTR for each group is calculated as follows:

$$\hat p_A=\frac{X_A}{n_A}$$


$$\hat p_B=\frac{X_B}{n_B}$$

Here, $p_A$ and $p_B$ represent the unknown population proportions, whereas $\hat p_A$ and $\hat p_B$ represent their corresponding sample estimates.

The difference between the two observed CTRs is expressed as:

$$\hat{\Delta}=\hat p_B-\hat p_A$$

This difference represents the estimated treatment effect in terms of CTR.

A positive value of $\hat{\Delta}$ indicates that the treatment version has a higher observed CTR, whereas a negative value indicates that the control version has a higher observed CTR.

**Statistical Framework for Fixed Sample Size A/B Testing**

The statistical framework is based on comparing two independent population proportions.

The number of clicks in each experimental group can be modelled using a binomial distribution:
$$X_A\sim Binomial(n_A,p_A)$$

$$X_B\sim Binomial(n_B,p_B)$$

The corresponding probability mass functions are:
$$
P(X_A=x_A)=
\binom{n_A}{x_A}
p_A^{x_A}(1-p_A)^{n_A-x_A}
$$

$$
P(X_B=x_B)=
\binom{n_B}{x_B}
p_B^{x_B}(1-p_B)^{n_B-x_B}
$$

Assuming that the two experimental groups are independent, their click observations are modelled independently.

The objective is to statistically evaluate whether the population CTRs differ significantly.

Formulation of Statistical Hypotheses
A two-sided hypothesis test is considered to examine whether the population CTRs of the control and treatment groups are significantly different.

The hypotheses are formulated as follows:

Null Hypothesis $H_0$

The null hypothesis assumes that there is no difference between the population CTRs of the two experimental groups.

$H_0: p_A - p_B = 0$

Under the null hypothesis, the treatment version does not produce a statistically significant change in CTR compared with the control version.

Alternative Hypothesis $H_1$

The alternative hypothesis assumes that the population CTRs of the two experimental groups are different.

$H_0: p_A - p_B \ne 0$

Under the alternative hypothesis, the treatment version produces a statistically significant change in CTR, either positively or negatively, compared with the control version.

The two-sided formulation allows the experiment to detect both improvements and deteriorations in CTR without assuming the direction of the treatment effect in advance.

**Significance Level and False Positive Rate**

The significance level, denoted by $\alpha$, represents the maximum acceptable probability of rejecting the null hypothesis when it is actually true.

In this study, the significance level is specified as:

$$\alpha = 0.05$$

This corresponds to a 5% False Positive Rate.

Since the experiment employs a two-sided hypothesis test, the significance level is divided equally between the two tails of the sampling distribution:


$$\frac{\alpha}{2}=0.025$$

Under the standard normal approximation, the corresponding critical values are:

$${Z_{\alpha/2}=\pm1.96}$$

Therefore, the null hypothesis will be rejected if the absolute value of the calculated test statistic exceeds 1.96

FPR stands for False Positive Rate. It is the probability of incorrectly declaring that Version B performs better than Version A when, in reality, there is no actual difference.


**Statistical Power**

Statistical power refers to the probability of correctly rejecting the null hypothesis when a true difference exists between the population CTRs.

It is mathematically expressed as:

$$Power=1-\beta$$

where $\beta$ represents the probability of Type II Error.

For the proposed experiment, statistical power is assumed to be 80%.

$${1-\beta=0.80}$$

Thus,


$$\beta=0.20$$

An 80% statistical power indicates that the experiment has an 80% probability of detecting a specified true difference in population CTRs, provided the underlying assumptions and design parameters hold.



**Minimum Detectable Effect (MDE)**

The Minimum Detectable Effect (MDE) represents the smallest difference between the two population CTRs that the experiment is designed to detect at a specified significance level and statistical power.

It can be expressed as:

$$\Delta=p_B-p_A$$

For experimental design, the absolute magnitude of the target difference is generally considered:

$$MDE=|p_B-p_A|$$

The MDE, significance level, and statistical power are important design parameters for determining the required sample size of the experiment.


**Determination of Fixed Sample Size**

In the fixed sample size approach, the required number of impressions is determined before conducting the experiment.

The sample size $N$ calculation depends on the following parameters:
1. Expected baseline CTR $p_A$.
2. Expected treatment CTR $p_B$.
3. Significance level $\alpha$.
4. Statistical power $1-\beta$.
5. Minimum Detectable Effect (MDE).

Once these parameters are specified, the required sample size can be estimated using the sample size formula (given below) for comparing two independent proportions.

$$ N = \frac{2\sigma^{2} (Z_{1 - \frac{\alpha}{2}} + Z_{1 - \beta})^2}{MDE^2} $$

The experiment is conducted until the predetermined sample size is achieved in both groups.


![Figure2](figures/figure2.png)


<div style="page-break-after: always;"></div>


**Sequential Testing in A/B Testing**

Sequential testing is a statistical approach used in A/B testing in which experimental data are evaluated at multiple stages during the experiment rather than only at the end of a predetermined sample size. Unlike traditional fixed-horizon testing, where the sample size is established before the experiment begins and statistical inference is performed after collecting all observations, sequential testing allows researchers to monitor the accumulated evidence as new observations become available.

In digital experimentation, such as website optimization, online advertising, and application development, continuous monitoring of experimental results is often desirable. Researchers and businesses may want to determine whether a modified version of a product performs better than the existing version without unnecessarily continuing the experiment.

Sequential testing provides a framework for making decisions based on accumulating statistical evidence. Depending on the evidence obtained, the experiment may be stopped early, continued for additional observations, or terminated when a predefined statistical boundary is reached.

However, repeatedly examining experimental results introduces important statistical challenges, particularly the phenomena known as peeking and early stopping. These phenomena must be understood because inappropriate monitoring and stopping decisions can increase the probability of false-positive results.


**Peeking Phenomenon in A/B Testing**

Peeking refers to the practice of repeatedly examining the statistical results of an ongoing experiment before the predetermined sample size has been reached.

In traditional fixed-horizon A/B testing, researchers are expected to determine the sample size in advance and conduct the final hypothesis test after collecting the required observations.

However, in practical applications, researchers may examine the experimental results every day or after every batch of impressions to determine whether one version is performing better.

**Early Stopping in A/B Testing**

Early stopping for futility occurs when the experiment is unlikely to demonstrate the desired treatment effect even if additional observations are collected.

For example, suppose the objective is to detect an improvement in CTR of at least one percentage point.

If the interim results indicate that the treatment effect is very small and the conditional probability of achieving the desired result is sufficiently low, the experiment may be stopped for futility.

Futility stopping is generally used to avoid wasting time and resources on experiments that are unlikely to produce meaningful results.

![Figure3](figures/figure3.png)


<div style="page-break-after: always;"></div>


### **SPRT Test**

**Sequential Probability Ratio Test (SPRT) for A/B Testing Using Binomial Distribution**

The Sequential Probability Ratio Test (SPRT) is a statistical hypothesis testing technique used to make decisions continuously as new observations become available. Unlike the Fixed Sample Size A/B Testing approach, where the sample size is determined before the experiment begins, SPRT evaluates the accumulated evidence after each new observation or batch of observations.

In conventional A/B testing, the experiment is conducted until a predetermined number of impressions is collected in both the control and treatment groups. Statistical inference is then performed using the collected data.

However, in many practical applications, collecting a large number of observations can be time-consuming and computationally expensive. SPRT provides an alternative approach by allowing researchers to evaluate the evidence sequentially and terminate the experiment as soon as sufficient statistical evidence is obtained in favour of either hypothesis.

In this study, SPRT is applied to compare the Click-Through Rates (CTR) of two independent experimental groups using the binomial probability distribution.

The two experimental groups are defined as follows:
- Group A (Control): Represents the existing version of a webpage, advertisement, or application.
- Group B (Treatment): Represents the modified version introduced to evaluate its impact on CTR.

The primary objective is to determine whether the modification introduced in Group B produces a statistically significant difference in CTR compared with Group A.

The Sequential Probability Ratio Test (SPRT) tests a population proportion by evaluating data sequentially, rather than waiting for a fixed sample size.

Suppose we test a conversion rate or CTR.

**Define hypotheses**

Let $p$ be the true population proportion.

$$H_0:p=p_0$$

$$H_1:p=p_1$$

where $p_0$ and $p_1$ are the proportions specified under the null and alternative hypotheses.

**Likelihood function**

For $n$ independent Bernoulli observations, let $X_n=\sum_{i=1}^{n}x_i$ be the total number of successes.

The likelihood under $H_0$ is

$$L_0=p_0^{X_n}(1-p_0)^{n-X_n}$$

The likelihood under $H_1$ is

$$L_1=p_1^{X_n}(1-p_1)^{n-X_n}$$

**SPRT likelihood ratio function**

The likelihood ratio is

$$\Lambda_n=\frac{L_1}{L_0}$$

Substituting the likelihood functions:

$$
\Lambda_n=
\left(\frac{p_1}{p_0}\right)^{X_n}
\left(\frac{1-p_1}{1-p_0}\right)^{n-X_n}
$$

The log-likelihood ratio is

$$
\log\Lambda_n=
X_n\log\left(\frac{p_1}{p_0}\right)
+(n-X_n)\log\left(\frac{1-p_1}{1-p_0}\right)
$$

**SPRT decision boundaries**

Choose:
- $\alpha$ = probability of Type I error.
- $\beta$ = probability of Type II error.

The approximate likelihood-ratio boundaries are
$$
A=log(\frac{1-\beta}{\alpha}),
\qquad
B=log(\frac{\beta}{1-\alpha})
$$


* $\Lambda_n\ge A$, 	Accept evidence for $H_1$
* $\Lambda_n\le B$,	Accept evidence for $H_0$
* $B<\Lambda_n<A$, 	    Continue collecting data


These boundaries are approximate for the standard SPRT; the test stops when a boundary is crossed.

<div style="page-break-after: always;"></div>


### **Simulation Analysis**

We conducted a simulation study to evaluate the statistical effectiveness and robustness of the Fixed-Horizon and Sequential Probability Ratio Test (SPRT) methods. The simulation was initiated by considering two hypothetical advertising campaigns with different Click-Through Rates (CTR). The control campaign was assigned a CTR of $p_A=0.50$, while the treatment campaign was assigned a CTR of $p_B=0.52$.

A binomial data-generating process was employed to simulate the click observations for both campaigns. This approach was selected because each impression represents a binary outcome, either a click or a non-click. The simulated data were designed to replicate the click behaviour observed when testing two different versions of an advertisement in a real-world experimental environment.

The generated datasets were subsequently used to evaluate and compare the performance of the Fixed-Horizon and SPRT methods in terms of statistical effectiveness, decision accuracy, sample-size requirements, and robustness under different experimental conditions.

We conducted 10,000 simulation replications, with each replication consisting of a sample size of 10,000 observations for each experimental variant. The primary objective was to examine whether the sampling distributions of the estimated Click-Through Rates (CTR) approximately followed a normal distribution, in accordance with the Central Limit Theorem (CLT). This simulation-based approach was adopted to validate the normal approximation under repeated sampling and to establish a reliable statistical foundation for the subsequent A/B testing analysis.

The results indicated that the estimated mean CTR was approximately 0.0499 for the control variant and 0.0526 for the treatment variant. These estimates were consistent with the expected CTR values used in the simulation. The repeated sampling procedure provided an empirical basis for assessing the approximate normality of the sampling distributions, thereby supporting the application of normal-based statistical methods in the Fixed-Horizon A/B testing framework.

#### **Mean of Control and Treatment Distributions (Table-1)**

| Distribution | Mean |
|:---|---:|
| Control | 0.049921 |
| Treatment | 0.052637 |

![Figure1](figures/figure1.png)

**Evaluation of Fixed-Horizon A/B Testing Under the Null Hypothesis (A/A Testing)**

To evaluate the statistical validity of the Fixed-Horizon A/B Testing framework, we conducted a simulation study consisting of 1,000 independent A/A testing experiments. In each experiment, both the control and treatment groups were assigned the same underlying CTR  $p_{\text{control}}=p_{\text{treatment}}$, ensuring that no actual treatment effect existed. A fixed sample size of 120,000 observations was considered for each experimental group.

The primary objective of this simulation was to examine the distribution of p-values under the null hypothesis and assess whether the testing procedure maintained the specified False Positive Rate (FPR).

The simulation results indicated that the p-values were approximately uniformly distributed between 0 and 1. Furthermore, the empirical FPR was observed to be approximately 0.048, consistent with the predefined significance level of $\alpha=0.05$. The corresponding cumulative distribution function (CDF) plot exhibited an approximately straight diagonal line, providing further evidence of uniformity in the p-value distribution.

These findings suggest that the Fixed-Horizon A/B Testing framework maintains the nominal Type I Error rate under the null hypothesis and provides statistically reliable results when the experiment is conducted using a predetermined sample size without premature stopping.

#### **AA Test (FPR) Simulation Results Table-2**

| Metric | Value | 
|:---|---:|
| False Positive Rate (FPR) | 0.048 |
| Average Sample Size | 120000.0 |


![Figure2](figures/figure4.png)

**Evaluation of Statistical Power Under the Alternative Hypothesis (A/B Testing)**

To evaluate the ability of the Fixed-Horizon A/B Testing framework to detect an actual difference between two experimental variants, we conducted a simulation study consisting of 1,000 independent A/B testing experiments under the alternative hypothesis.

In this setting, the control and treatment groups were assigned different underlying CTR values, such that:

$$
H_1:p_{\text{control}}\neq p_{\text{treatment}}
$$

Unlike the A/A testing scenario, where both variants have identical CTRs, this experiment introduces a genuine difference between the two groups to assess the ability of the statistical testing procedure to identify the treatment effect.

The p-values obtained from the 1,000 simulation replications were examined to evaluate the detection capability of the testing framework. Under the alternative hypothesis, the p-value distribution was expected to concentrate towards smaller values, indicating stronger evidence against the null hypothesis.

The simulation results produced an estimated statistical power of approximately 0.812 (81%), which is slightly higher than the predefined target power of 0.80 (80%). This indicates that, for the selected sample size and treatment effect, the Fixed-Horizon testing framework successfully detected the difference between the two experimental variants in approximately 85% of the simulation replications.

Overall, these findings demonstrate that the Fixed-Horizon A/B Testing framework provides satisfactory statistical power while maintaining the nominal 5% False Positive Rate under the null hypothesis.


#### **AB Test (Power) Simulation Results Table-3**

| Metric | Value |
|:---|---:|
| Power Rate | 0.812 |
| Average Sample Size | 120000.0 |

![Figure6](figures/figure6.png)


**A/A Testing with Early Stopping: Effect of Peeking on False Positive Rate**

To investigate the statistical consequences of repeated monitoring and premature termination, we extended the simulation study by introducing an early-stopping mechanism into the A/A testing framework.

Unlike the conventional Fixed-Horizon approach, where statistical inference is performed only after reaching the predetermined sample size, the early-stopping framework allows repeated examination of experimental results during the data collection process.

For this experiment, we again conducted 1,000 independent A/A testing simulations, maintaining identical underlying CTRs for the control and treatment groups. The peeking frequency was set to 10, meaning that the statistical significance was evaluated at 10 interim analysis points during the experiment.

An early-stopping rule was implemented whereby the experiment was terminated whenever the calculated test statistic crossed the predefined critical significance boundary at any interim analysis. Since both experimental variants had identical underlying CTRs, any statistically significant result represented a false-positive finding.

The simulation results demonstrated a substantial inflation in the False Positive Rate, which increased to approximately 18.2%, compared with the nominal significance level of 5%.

This increase indicates that repeatedly examining intermediate results and stopping the experiment as soon as statistical significance is achieved substantially increases the probability of incorrectly rejecting the null hypothesis.

The findings demonstrate the statistical limitations of applying conventional fixed-horizon significance tests with unadjusted repeated monitoring. Although the original Fixed-Horizon framework maintains the desired Type I Error rate when the predetermined sample size is respected, introducing an unadjusted early-stopping mechanism compromises this statistical validity.

Consequently, these results highlight the importance of employing appropriately designed sequential testing procedures, such as the Sequential Probability Ratio Test (SPRT), to control statistical errors while allowing continuous monitoring and early termination of experiments.


<br><br> 

#### **AA Test with Early Stopping (FPR) Simulation Results Table-4**

| Metric | Value |
|:---|---:|
| False Positive Rate (FPR) | 0.182 |
| Average Sample Size | 106668.0 |


#### **Simulation Results for Different Peeking Frequencies Table-5**

| Peeking Frequency | False Positive Rate (FPR) | Average Sample Size |
|:---:|---:|---:|
| 1 | 0.055 | 120000.000 |
| 2 | 0.094 | 116940.000 |
| 3 | 0.114 | 114520.000 |
| 4 | 0.129 | 112560.000 |
| 5 | 0.129 | 111576.000 |
| 6 | 0.186 | 107480.000 |
| 7 | 0.165 | 108737.049 |
| 8 | 0.177 | 107445.000 |
| 9 | 0.197 | 106013.262 |
| 10 | 0.213 | 104292.000 |


![Figure5](figures/figure5.png)

**Evaluation of False Positive Rate (FPR) Under the Null Hypothesis: SPRT A/A Testing**

To evaluate the statistical validity of SPRT under the null hypothesis, we conducted an A/A testing simulation in which both the control and treatment groups were assigned identical underlying CTR values. Since both variants represented the same underlying population, no actual treatment effect existed.

The SPRT procedure was implemented using an early-stopping mechanism based on predefined likelihood-ratio decision boundaries. As new observations became available, the cumulative SPRT score was recalculated and compared against the upper and lower stopping boundaries.

If the likelihood ratio crossed either boundary, the experiment was terminated and the corresponding statistical decision was recorded. Otherwise, additional observations were collected, and the process continued.

The simulation was performed across 10 independent runs, each consisting of 1,000 replications. The primary objective was to examine whether SPRT could maintain the desired Type I Error probability while allowing early termination of experiments.

The simulation results indicated that the empirical False Positive Rate was approximately 0.045 (4.5%), which was close to the predefined significance level of 0.05 (5%). This suggests that the SPRT procedure maintained an acceptable level of Type I Error under the null hypothesis.

Furthermore, the average sample size required to reach a statistical decision was approximately 24,000 observations per experimental group. 

#### **SPRT AA Test Simulation Results Table-6**

| Trial | False Positive Rate (FPR) | Average Sample Size |
|:---:|---:|---:|
| 0 | 0.045 | 25074.0 |
| 1 | 0.047 | 23837.0 |
| 2 | 0.040 | 24758.0 |
| 3 | 0.045 | 24223.0 |
| 4 | 0.044 | 24800.0 |
| 5 | 0.059 | 24968.0 |
| 6 | 0.059 | 23972.0 |
| 7 | 0.042 | 24610.0 |
| 8 | 0.060 | 26115.0 |
| 9 | 0.042 | 25085.0 |


![Figure8](figures/figure8.png)

**Evaluation of Statistical Power Under the Alternative Hypothesis: SPRT A/B Testing**

To evaluate the ability of the Sequential Probability Ratio Test (SPRT) to detect a genuine difference between two experimental variants, we conducted a simulation study under the alternative hypothesis using an A/B testing framework.

Unlike the A/A testing experiment, in which both groups were assigned identical underlying CTR values, the A/B testing simulation considered two different variants with distinct CTRs for the control and treatment groups. This enabled us to examine the detection capability of SPRT when an actual treatment effect exists.

The experiment was implemented using a sequential monitoring mechanism with predefined likelihood-ratio decision boundaries. As new observations became available, the cumulative SPRT statistic was updated and compared against the upper and lower stopping boundaries. If either boundary was crossed, the experiment was terminated and the corresponding statistical decision was recorded. Otherwise, additional observations were collected until a stopping condition was satisfied.

To obtain reliable estimates of statistical performance, the simulation was conducted over 10 independent runs, with each run consisting of 1,000 simulation replications. The primary objective was to estimate the average statistical power and the average sample size required by SPRT to detect the difference between the two experimental variants.

The simulation results indicated that SPRT achieved an average statistical power of approximately 82.1%, which is slightly higher than the predefined target power of 80%. This suggests that the sequential testing procedure successfully detected the specified treatment effect in approximately 82.1% of the simulated experiments.

Furthermore, the average sample size required to reach a statistical decision was approximately 33,000 observations per experimental group. This indicates that SPRT was able to achieve the desired detection capability while employing sequential monitoring and an early-stopping mechanism.

Overall, the results demonstrate that SPRT achieved satisfactory statistical power under the alternative hypothesis. When considered alongside the A/A testing results, which produced an empirical False Positive Rate of approximately 4.5%, these findings suggest that SPRT maintained an acceptable balance between Type I Error control and the ability to detect genuine treatment effects under the specified simulation conditions.

#### **SPRT AB Test Simulation Results Table-7**

| Trial | Power Rate | Average Sample Size |
|:---:|---:|---:|
| 0 | 0.814 | 33905.0 |
| 1 | 0.800 | 33905.0 |
| 2 | 0.798 | 34510.0 |
| 3 | 0.812 | 32612.0 |
| 4 | 0.830 | 34290.0 |
| 5 | 0.842 | 33526.0 |
| 6 | 0.829 | 33204.0 |
| 7 | 0.795 | 32194.0 |
| 8 | 0.816 | 34475.0 |
| 9 | 0.826 | 33927.0 |

![Figure9](figures/figure9.png)

<div style="page-break-after: always;"></div>

### **Conclusion** 

Based on the simulation results, it can be concluded that the Sequential Probability Ratio Test (SPRT) offers a statistically efficient alternative to the conventional Fixed-Horizon A/B Testing framework, particularly in terms of sample-size requirements and testing duration. The findings indicate that SPRT can substantially reduce the number of observations required to reach a statistical decision while maintaining an acceptable level of False Positive Rate (FPR) and statistical power within the predefined experimental parameters.

The simulation analysis further reveals that the sample-size requirements of SPRT depend on the underlying treatment effect. In particular, SPRT requires a different number of observations depending on the extent of the difference between the control and treatment variants. When the experimental evidence is sufficient to distinguish between the two variants, the sequential procedure can terminate the experiment early. Conversely, detecting a genuine treatment effect may require additional observations to accumulate sufficient statistical evidence to cross the predefined decision boundaries.

Overall, the findings suggest that SPRT has considerable potential to improve the efficiency of A/B testing within digital experimentation frameworks, particularly for evaluating Click-Through Rates (CTR). Its ability to continuously monitor experimental outcomes and make decisions based on accumulated statistical evidence makes it a useful alternative to traditional fixed-horizon testing. Therefore, SPRT can help reduce experimentation time and potentially lower the resources required for digital optimization while preserving statistical reliability.

In conclusion, the study demonstrates that sequential testing, particularly SPRT, provides a promising statistical framework for conducting more efficient A/B experiments. Its application can be particularly beneficial in digital analytics environments where large volumes of user impressions and click observations are continuously generated.


<div style="page-break-after: always;"></div>

**References**

The following references can be included in your thesis bibliography. They are formatted in APA 7th-edition style.

1. Wald (1945) – Foundational reference for SPRT Wald, A. (1945). Sequential tests of statistical hypotheses. The Annals of Mathematical Statistics, 16(2), 117–186. 
https://doi.org/10.1214/aoms/1177731118

2. Kohavi, Tang, and Xu (2020) – A/B testing and online experimentation Kohavi, R., Tang, D., & Xu, Y. (2020). Trustworthy online controlled experiments: A practical guide to A/B testing. Cambridge University Press.
https://doi.org/10.1017/9781108653985

3. Johari, Pekelis, and Walsh (2017) – Sequential inference and peeking Johari, R., Pekelis, L., & Walsh, D. J. (2017). Peeking at A/B tests: Why it matters, and what to do about it. Proceedings of the 23rd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 1517–1525.
https://doi.org/10.1145/3097983.3097992

4. Larsen et al. (2024) – Statistical challenges in online experimentation Larsen, N., Stallrich, J., Sengupta, S., Deng, A., Kohavi, R., & Stevens, N. T. (2024). Statistical challenges in online controlled experiments: A review of A/B testing methodology. The American Statistician, 78(2), 135–149.

https://doi.org/10.1080/00031305.2023.2257237

5. Kohavi and Longbotham (2023) – Online controlled experiments
Kohavi, R., & Longbotham, R. (2023). Online controlled experiments and A/B testing. In Encyclopedia of machine learning and data science. Springer.
https://doi.org/10.1007/978-1-4899-7502-7_891-2


<div style="page-break-after: always;"></div>

**Appendix**

**Code for CTR Simulation**

```python

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import scipy as sp


class clickGenerator:

    def __init__(self, ctr):
        self.ctr = ctr
        #self.click_sample_size = click_sample_size

    # click binomial function generator

    def generateClicks(self, click_sample_size):
        return np.random.binomial(n=1, p=self.ctr, size=click_sample_size)


v_A = clickGenerator(0.05)
v_B = clickGenerator(0.0525)

def CLT_simulation(control, treatment, dump_size, simulation_trials):
    
    ctr_control_distribution = np.zeros(simulation_trials)
    ctr_treatment_distribution = np.zeros(simulation_trials)

    for i in range(simulation_trials):
        
        control_sample = control.generateClicks(dump_size)
        treatment_sample = treatment.generateClicks(dump_size)
        control_mean = control_sample.mean()
        treatment_mean = treatment_sample.mean()

        ctr_control_distribution[i] = control_mean
        ctr_treatment_distribution[i] = treatment_mean

    return ctr_control_distribution, ctr_treatment_distribution

def distribution_plot(ctr_control_distribution,
                     ctr_treatment_distribution,
                     control_mean,
                     treatment_mean):
        
        fig, axs = plt.subplots(figsize=(10, 4))
        sns.kdeplot(x=ctr_control_distribution, color="red", alpha=0.3, fill=True, label="Control")
        sns.kdeplot(x=ctr_treatment_distribution, color="green", alpha=0.3, fill=True,label="Treatment")
        axs.axvline(control_mean, color="k", linestyle="--", label=f"Control {np.round(control_mean,4)}")
        axs.axvline(treatment_mean, color="k", linestyle="-.", label=f"Treatment {np.round(treatment_mean,4)}")
        axs.legend()
        fig.suptitle("Control VS Treatment Distribution", weight="bold");
        return fig

np.random.seed(1010)
dump_size = 1000
simulation_trials = 10000
ctr_control_distribution, ctr_treatment_distribution = CLT_simulation(control=v_A, 
                                                                      treatment=v_B, 
                                                                      dump_size=dump_size,
                                                                      simulation_trials = simulation_trials)
control_mean = ctr_control_distribution.mean()
treatment_mean = ctr_treatment_distribution.mean()

print(f"Control Distribution Mean: {control_mean}")
print(f"Treatment Distribution Mean: {treatment_mean}")

_ = distribution_plot(ctr_control_distribution=ctr_control_distribution,
                      ctr_treatment_distribution = ctr_treatment_distribution,
                      control_mean=control_mean,
                      treatment_mean=treatment_mean)

```


<div style="page-break-after: always;"></div>

**Code for ABTesting Simulation**

```python

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import scipy as sp

class clickGenerator:

    def __init__(self, ctr):
        self.ctr = ctr
        #self.click_sample_size = click_sample_size

    # click binomial function generator

    def generateClicks(self, click_sample_size):
        return np.random.binomial(n=1, p=self.ctr, size=click_sample_size)

control_version = clickGenerator(0.05)
treatment_version = clickGenerator(0.0525)

class ABTest:

    def __init__(self,seed_value, early_stopping, total_sample_size, version_A, version_B ):
        self.seed_value = seed_value
        self.early_stopping = early_stopping
        #self.p_threshold = p_threshold
        self.total_sample_size = total_sample_size
        #self.peeking_freq = peeking_freq
        self.version_A = version_A
        self.version_B = version_B

    @staticmethod
    def sample_size_func(ctr, significance_level, power, mde):
        
        #ctr = 0.05
        #significance_level = 0.05
        #power = 0.80
        #mde = 0.0025
        z_alpha = sp.stats.norm.ppf(1 - (significance_level / 2))
        z_beta = sp.stats.norm.ppf(power)
        variance = ctr * (1 - ctr)
        sample_size = (2 * (z_alpha + z_beta)**2  * variance)/ (mde**2) 

        #self.sample_size = sample_size
        print(f"Sample size needed is {int(sample_size)} per variation")

    def cdf_func(self,p_values):
        return np.sort(p_values), np.arange(len(p_values)) / len(p_values)
    
    def z_score_func(self, sample_A, sample_B):
        
        x_A = sample_A.sum()
        x_B = sample_B.sum()
        n_A = sample_A.size
        n_B = sample_B.size
        p_A = (x_A / n_A)
        p_B = (x_B / n_B)
        p_hat = (x_A + x_B) / (n_A + n_B)

        SE = np.sqrt((p_hat * (1 - p_hat)) * ((1/n_A) + (1/n_B)))
        Z_Value = (p_A - p_B) / SE
        P_Value = sp.stats.norm.sf(abs(Z_Value)) * 2

        return Z_Value, P_Value   

    # func abtest for every step of peeking and record results
    def abtesting_func(self, p_threshold, peeking_freq):
          
          np.random.seed(self.seed_value)
          sample_range = np.linspace(0, self.total_sample_size, peeking_freq+1, dtype=int)
          sample_control_bag = np.array([])
          sample_treatment_bag = np.array([])
          sample_range_len = len(sample_range)
          sample_size_bag = np.zeros(sample_range_len)
          p_value_log = np.zeros(sample_range_len)
          z_value_log = np.zeros(sample_range_len)
          control_ctr = np.zeros(sample_range_len)
          treatment_ctr = np.zeros(sample_range_len)


          #p_value_log
          #print(early_stopping) 
          i = 0
          for _ in range(sample_range_len - 1):
              
              #print(sample_range[i+1], sample_range[i])
              sample_size = sample_range[i+1] - sample_range[i]
              #print(sample_size)
              sample_control = self.version_A.generateClicks(sample_size)
              sample_treatment = self.version_B.generateClicks(sample_size)
              sample_control_bag = np.concatenate((sample_control_bag, sample_control))
              sample_treatment_bag = np.concatenate((sample_treatment_bag, sample_treatment))
              sample_size_bag[i+1] = sample_range[i+1]
              control_ctr[i+1] = sample_control_bag.mean()
              treatment_ctr[i+1] = sample_treatment_bag.mean()
              z_value, p_value = self.z_score_func(sample_control_bag, sample_treatment_bag)
              z_value_log[i+1] = z_value
              p_value_log[i+1] = p_value
              total_sample_size_ =  sample_range[i+1]
              #print(sample_range[i+1], z_value, p_value)
              if self.early_stopping == True:
                if p_value <= p_threshold:
                    #print(p_value)
                    break
    
              i = i + 1 
          
          sample_size_bag_ = sample_size_bag[sample_size_bag !=0]
          p_value_log_ = p_value_log[p_value_log != 0]
          z_value_log_ = z_value_log[z_value_log != 0]
          control_ctr_ = control_ctr[control_ctr != 0]
          treatment_ctr_ = treatment_ctr[treatment_ctr != 0]
          return p_value_log_, z_value_log_, control_ctr_, treatment_ctr_, total_sample_size_, sample_size_bag_

    def simulation_func(self, simulation_trials, p_threshold, peeking_freq):

        #sim_logs = []
        p_distribution = np.zeros(simulation_trials)
        p_hits = 0
        total_sample_size = 0
        #simulation_trials = 1000
        for i in range(simulation_trials):
            p_value_log, z_value_log, control_ctr, treatment_ctr, sample_size, _ = self.abtesting_func(p_threshold,peeking_freq)
            #print(p_value_log)
            #print(treatment_ctr)
            #print(control_ctr)
            #sim_logs.append(z_value_log)
            p_distribution[i] = p_value_log[-1]
            total_sample_size = total_sample_size + sample_size
            if p_value_log[-1] <= 0.05:
                p_hits = p_hits + 1

        #sim_logs_ = np.array(sim_logs, dtype=object)
        p_sim_ratio = (p_hits/ simulation_trials)
        average_sample_size = (total_sample_size/ simulation_trials)
        #print(p_value_log[0])
        return p_sim_ratio, average_sample_size, p_distribution



def sequential_plot(sample_range, 
                    p_value_log, 
                    z_value_log, 
                    control_ctr, 
                    treatment_ctr):
    fig, axs = plt.subplots(3, 1, figsize=(8, 6))
    sns.lineplot(x=sample_range, y=p_value_log, color="mediumpurple",linewidth=2.5, alpha=1.0, ax=axs[0])
    axs[0].axhline(0.05, color="k", linestyle="--", label="0.05")
    axs[0].set_ylim(0.01, 1.0)
    axs[0].set_xlim(0, 122000)
    axs[0].legend()
    #axs[0].set(xlabel="sample size")
    axs[0].set(ylabel="p-value")
    axs[0].set_title("sequential p-value", weight=None)
    sns.lineplot(x=sample_range, y=z_value_log, color="mediumpurple",linewidth=2.5, alpha=1.0, ax=axs[1])
    axs[1].axhline(1.96, color="k", linestyle="--", label="+/- 1.96")
    axs[1].axhline(-1.96, color="k", linestyle="--")
    axs[1].set_ylim(-5, 5)
    #axs[1].set(xlabel="sample size")
    axs[1].set(ylabel="z-score")
    axs[1].set_title("sequential z-score", weight=None)
    axs[1].legend()
    sns.lineplot(x=sample_range, y=control_ctr, color="mediumpurple",linewidth=2.5, alpha=1.0, label="control", ax=axs[2])
    sns.lineplot(x=sample_range, y=treatment_ctr, color="violet",linewidth=2.5, label="treatment", alpha=1.0, ax=axs[2])
    axs[2].set_ylim(0.04, 0.06)
    axs[2].set(xlabel="sample size")
    axs[2].set(ylabel="CTR")
    axs[2].set_title("sequential CTR", weight=None)

    plt.tight_layout()

    return fig

def abtest_dignostic_plot(abtest, 
                          p_value_log, 
                          fh_sample_size,  
                          average_sample_size, 
                          title):
        
        p_x, p_y  = abtest.cdf_func(p_value_log)

        fig, ax = plt.subplots(1, 3, figsize=(8.5,3.0))
        sns.histplot(p_value_log, bins=20, stat='probability', color="mediumpurple", label="Histogram", ax=ax[0])
        ax[0].set_ylim(0.00, 0.2)
        ax[0].set_ylabel("p-values")
        ax[0].set_xlabel("Histogram")

        sns.lineplot(x=p_x, y=p_y, color="mediumpurple",linewidth=2.5, alpha=1.0, ax=ax[1])
        sns.lineplot(x=p_x, y=p_x,color="black",linewidth=1.5, alpha=0.6, ax=ax[1])
        ax[1].set_xlabel("CDF")

        sns.barplot(x=["Fixed Horizon", "Sequential"], 
                    y=[fh_sample_size, int(average_sample_size)],
                    color="mediumpurple", alpha = 1.0,  ax=ax[2])
        ax[2].set_ylabel("sample-size")
        fig.suptitle(title)
        plt.tight_layout();

        return fig

# Sample size calculation

ABTest.sample_size_func(ctr = 0.05,
                        significance_level = 0.05,
                        power = 0.80,
                        mde = 0.0025)


exp_sample_size = 120000

# Peeking in AB Test without Early stopping
aatest_wo_es_fpr = ABTest(seed_value=1010,
                          early_stopping = False,
                          total_sample_size=exp_sample_size,
                           version_A=control_version,
                           version_B=control_version)

abtest_wo_es_power = ABTest(seed_value=1010,
                          early_stopping = True,
                          total_sample_size=exp_sample_size,
                           version_A=control_version,
                           version_B=treatment_version)


# Peeking in AA Test without Early stopping
p_threshold = 0.05
peeking_freq = 10
p_value_log_, z_value_log_, control_ctr_, treatment_ctr_, total_sample_size_, sample_size_bag_ = aatest_wo_es_fpr.abtesting_func(p_threshold=0.05,
                                                                                                               peeking_freq=peeking_freq)
_ = sequential_plot(sample_range=sample_size_bag_,
                     p_value_log=p_value_log_, 
                     z_value_log=z_value_log_, 
                     control_ctr=control_ctr_, 
                     treatment_ctr=treatment_ctr_)


# Peeking in AB Test with Early stopping
p_threshold = 0.05
peeking_freq = 10
p_value_log_, z_value_log_, control_ctr_, treatment_ctr_, total_sample_size_, sample_size_bag_ = abtest_wo_es_power.abtesting_func(p_threshold=0.05,
                                                                                                                                   peeking_freq=peeking_freq)
_ = sequential_plot(sample_range=sample_size_bag_,
                     p_value_log=p_value_log_, 
                     z_value_log=z_value_log_, 
                     control_ctr=control_ctr_, 
                     treatment_ctr=treatment_ctr_)


# AA_test Simulation for FPR 
aatest_wo_es_fpr =  ABTest(seed_value=None,
                          early_stopping = False,
                          total_sample_size=exp_sample_size,
                           version_A=control_version,
                           version_B=control_version)

aatest_es_fpr =  ABTest(seed_value=None,
                          early_stopping = True,
                          total_sample_size=exp_sample_size,
                           version_A=control_version,
                           version_B=control_version)

abtest_wo_es_power =  ABTest(seed_value=None,
                             early_stopping = False,
                             total_sample_size=exp_sample_size,
                             version_A=control_version,
                             version_B=treatment_version)

abtest_es_power =  ABTest(seed_value=None,
                             early_stopping = True,
                             total_sample_size=exp_sample_size,
                             version_A=control_version,
                             version_B=treatment_version)


np.random.seed(1010)
sims_trials = 1000
p_threshold = 0.05
peeking_freq = 10
p_sim_ratio, average_sample_size, p_distribution = aatest_wo_es_fpr.simulation_func(simulation_trials=sims_trials, 
                                                                    p_threshold = p_threshold, 
                                                                    peeking_freq = peeking_freq)

_ = abtest_dignostic_plot(abtest=aatest_wo_es_fpr,
                          p_value_log=p_distribution, 
                          fh_sample_size=exp_sample_size,  
                          average_sample_size = average_sample_size, 
                          title = "AA_Test W/O Early Stopping (FPR)")

print(f"For {sims_trials} Simulation Trials FPR Rate : {p_sim_ratio} | Average Sample Size: {average_sample_size} ")


np.random.seed(1010)
sims_trials = 1000
p_threshold = 0.05
peeking_freq = 10
p_sim_ratio, average_sample_size, p_distribution = aatest_es_fpr.simulation_func(simulation_trials=sims_trials, 
                                                                    p_threshold = p_threshold, 
                                                                    peeking_freq = peeking_freq)

_ = abtest_dignostic_plot(abtest=aatest_es_fpr,
                          p_value_log=p_distribution, 
                          fh_sample_size=exp_sample_size,  
                          average_sample_size = average_sample_size, 
                          title = "AA_Test With Early Stopping (FPR)")
print(f"For {sims_trials} Simulation Trials FPR Rate : {p_sim_ratio} | Average Sample Size: {average_sample_size} ")



np.random.seed(1010)
sims_trials = 1000
p_threshold = 0.05
peeking_freq = 10
p_sim_ratio, average_sample_size, p_distribution = abtest_wo_es_power.simulation_func(simulation_trials=sims_trials, 
                                                                    p_threshold = p_threshold, 
                                                                    peeking_freq = peeking_freq)

_ = abtest_dignostic_plot(abtest=abtest_wo_es_power,
                          p_value_log=p_distribution, 
                          fh_sample_size=exp_sample_size,  
                          average_sample_size = average_sample_size, 
                          title = "AB_Test W/0 Early Stopping (Power)")
print(f"For {sims_trials} Simulation Trials Power Rate : {p_sim_ratio} | Average Sample Size: {average_sample_size} ")


np.random.seed(1010)
sims_trials = 1000
p_threshold = 0.05
peeking_freq = 10
p_sim_ratio, average_sample_size, p_distribution = abtest_es_power.simulation_func(simulation_trials=sims_trials, 
                                                                    p_threshold = p_threshold, 
                                                                    peeking_freq = peeking_freq)

_ = abtest_dignostic_plot(abtest=abtest_es_power,
                          p_value_log=p_distribution, 
                          fh_sample_size=exp_sample_size,  
                          average_sample_size = average_sample_size, 
                          title = "AB_Test With Early Stopping (Power)")
print(f"For {sims_trials} Simulation Trials Power Rate : {p_sim_ratio} | Average Sample Size: {average_sample_size} ")


# What happens are we peek more (our FPR rate continue to inflate)

sims_trials = 1000
p_threshold = 0.05
peeking_freq = 10
mean_fpr_rate = []
mean_sample_size = []

for freq in range(peeking_freq):
    
    p_sim_ratio, average_sample_size, p_distribution = aatest_es_fpr.simulation_func(simulation_trials=sims_trials, 
                                                                                     p_threshold = p_threshold, 
                                                                                    peeking_freq = freq+1)

    
    mean_fpr_rate.append(p_sim_ratio)
    mean_sample_size.append(average_sample_size)
    print(f"For Peeking Frequency: {freq+1} | {sims_trials} Simulation Trials FPR Rate : {p_sim_ratio} | Average Sample Size: {average_sample_size} ")

```


<div style="page-break-after: always;"></div>

**Code for SPRT Testing Simulation**

```python

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import scipy as sp

class clickGenerator:

    def __init__(self, ctr):
        self.ctr = ctr
        #self.click_sample_size = click_sample_size

    # click binomial function generator

    def generateClicks(self, click_sample_size):
        return np.random.binomial(n=1, p=self.ctr, size=click_sample_size)

control_version = clickGenerator(0.05)
treatment_version = clickGenerator(0.0525)

class SPRT_GST:

    def __init__(self,total_sample_size, dump_size, baseline_ctr, mde, test_version ):
        self.total_sample_size = total_sample_size
        self.dump_size = dump_size
        self.baseline_ctr = baseline_ctr
        self.mde = mde
        self.test_version = test_version

    @staticmethod
    def boundry_thresholds(alpha, beta):
        
        a = np.log( beta / (1-alpha) )
        b = np.log( (1-beta) / alpha )

        return np.round((a, b),4)
    
     
    def log_liklihood_ratio_binomial_func(self, baseline_ctr, mde, clicks, non_clicks):
        
        p1 = baseline_ctr + mde
        p0 = baseline_ctr

        part1 = clicks * np.log(p1/p0)
        part2 = non_clicks * np.log((1-p1)/(1-p0))

        log_delta = part1 + part2

        return log_delta

    def SPRT_Test(self, upper_boundry, lower_boundry):
         
         total_steps = int(self.total_sample_size/ self.dump_size)
         observed_data_logs = np.array([])
         sample_size = 0
         lambda_logs = np.zeros(total_steps)
         sample_size_bag = np.zeros(total_steps)
         

         for i in range(total_steps):
             
             sample_data = self.test_version.generateClicks(self.dump_size)
             sample_size = sample_size  +  self.dump_size 
             observed_data_logs = np.concatenate((observed_data_logs, sample_data))
             clicks = observed_data_logs.sum()
             non_clicks = len(observed_data_logs) - clicks

             lambda_ = self.log_liklihood_ratio_binomial_func(baseline_ctr=self.baseline_ctr,
                                                         mde=self.mde,
                                                         clicks=clicks,
                                                         non_clicks=non_clicks)
             #print(lambda_)
             sample_size_bag[i] = sample_size 
             lambda_logs[i] = lambda_
             #print(len(observed_data_logs))
        
             if lambda_ >= upper_boundry:
                  #print("Accept Alternative Hypothesis")
                  break
             elif lambda_ <= lower_boundry:
                  #print("Accept Null Hypothesis")
                  break
             else:
                 continue
    
         #print(lambda_logs)
         lambda_logs = lambda_logs[lambda_logs != 0]
         sample_size_bag = sample_size_bag[sample_size_bag !=0]
         used_sample_size = len(observed_data_logs)
         #print(lambda_logs)

         return lambda_logs, used_sample_size, sample_size_bag

    def sprt_simulation(self, simulation_trials, upper_boundry, lower_boundry):
        
        p_hits_b = 0
        p_hits_a = 0
        sample_size = 0
        for i in range(simulation_trials):
            
            lambda_logs, used_sample_size, _ =  self.SPRT_Test(upper_boundry,lower_boundry)
            critical_value = lambda_logs[-1]
            #print(critical_value)
            sample_size = sample_size + used_sample_size

            if critical_value >= b:
                p_hits_b = p_hits_b + 1
                #print(f"p_hits_b {p_hits_b}")
        
            if critical_value <=a:
                p_hits_a = p_hits_a + 1
                #print(f"p_hits_a {p_hits_a}")

        #print(p_hits_b, p_hits_a)
        fpr_rate = np.round(1 - (p_hits_a/simulation_trials),3)
        power_rate = np.round((p_hits_b/simulation_trials),3)
        average_sample_size = np.round((sample_size/simulation_trials),3)
        #print(fpr_rate, power_rate)
        return fpr_rate, power_rate, average_sample_size
    
total_sample_size = 120000
dump_size = 1000
baseline_ctr = 0.05
mde = 0.0025


aatest_sprt = SPRT_GST(total_sample_size=total_sample_size,
                        dump_size =dump_size,
                        baseline_ctr = baseline_ctr,
                        mde = mde,
                        test_version=control_version)

abtest_sprt = SPRT_GST(total_sample_size=total_sample_size,
                        dump_size =dump_size,
                        baseline_ctr = baseline_ctr,
                        mde = mde,
                        test_version=treatment_version)

def sprt_test_plot(sprt_test, upper_boundry, lower_boundry):
    lambda_logs, used_sample_size, sample_size_bag = sprt_test.SPRT_Test(upper_boundry,lower_boundry)
    fig, axs = plt.subplots(figsize=(10, 2.5))
    sns.lineplot(x=sample_size_bag, y=lambda_logs, color="mediumpurple",linewidth=2.5, alpha=1.0, ax=axs)
    axs.axhline(b, color="k", linestyle="--", label=b)
    axs.axhline(a, color="k", linestyle="--", label=a)
    axs.set_xlim(0, total_sample_size)
    axs.set_ylim(-5.5,5.5)
    axs.set(ylabel="sprt-score")
    axs.set_title("SPRT Cumulative Score", weight=None)
    axs.legend();

    return fig


# boundry threshold calculation 
alpha_significance_level =  0.05
beta = 0.20

a, b = aatest_sprt.boundry_thresholds(alpha=0.05, beta=0.20)
a = np.round(a, 3)
b = np.round(b, 3)

print(f"Critical Upper Boundry Threshold : {b}")
print(f"Critical Lower Boundry Threshold : {a}")


_ = sprt_test_plot(sprt_test = aatest_sprt, 
               upper_boundry = b,
               lower_boundry= a) 


_ = sprt_test_plot(sprt_test = abtest_sprt, 
                   upper_boundry = b,
                   lower_boundry= a) 


def sprt_analysis(sprt_test, trials, simulation_trials, upper_boundry, lower_boundry, analysis_type):
    
    for i in range(trials):
        fpr_rate, power_rate, average_sample_size = sprt_test.sprt_simulation(simulation_trials,
                                                                                upper_boundry, 
                                                                                lower_boundry)
        if analysis_type == "fpr": 
            print(f"Trial {i} | FPR Rate {fpr_rate} | Average Sample Size {average_sample_size}")
        if analysis_type == "power": 
            print(f"Trial {i} | Power Rate {power_rate} | Average Sample Size {average_sample_size}")
        

simulation_trials = 1000
trials = 10

sprt_analysis(sprt_test=aatest_sprt, 
              trials=trials,
              simulation_trials=simulation_trials,
              upper_boundry=b,
              lower_boundry=a,
              analysis_type="fpr")

simulation_trials = 1000
trials = 10

sprt_analysis(sprt_test=abtest_sprt, 
              trials=trials,
              simulation_trials=simulation_trials,
              upper_boundry=b,
              lower_boundry=a,
              analysis_type="power")

```


