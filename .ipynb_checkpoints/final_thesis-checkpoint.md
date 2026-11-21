### **Introduction**

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


### **Fixed Horizon A/B Testing** 

**Fxed Sample Size A/B Testing for Comparing Two Click-Through Rates (CTR)**

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

### **Simulation Analysis**

We conducted a simulation study to evaluate the statistical effectiveness and robustness of the Fixed-Horizon and Sequential Probability Ratio Test (SPRT) methods. The simulation was initiated by considering two hypothetical advertising campaigns with different Click-Through Rates (CTR). The control campaign was assigned a CTR of $p_A=0.50$, while the treatment campaign was assigned a CTR of $p_B=0.52$.

A binomial data-generating process was employed to simulate the click observations for both campaigns. This approach was selected because each impression represents a binary outcome, either a click or a non-click. The simulated data were designed to replicate the click behaviour observed when testing two different versions of an advertisement in a real-world experimental environment.

The generated datasets were subsequently used to evaluate and compare the performance of the Fixed-Horizon and SPRT methods in terms of statistical effectiveness, decision accuracy, sample-size requirements, and robustness under different experimental conditions.

We conducted 10,000 simulation replications, with each replication consisting of a sample size of 10,000 observations for each experimental variant. The primary objective was to examine whether the sampling distributions of the estimated Click-Through Rates (CTR) approximately followed a normal distribution, in accordance with the Central Limit Theorem (CLT). This simulation-based approach was adopted to validate the normal approximation under repeated sampling and to establish a reliable statistical foundation for the subsequent A/B testing analysis.

The results indicated that the estimated mean CTR was approximately 0.0499 for the control variant and 0.0526 for the treatment variant. These estimates were consistent with the expected CTR values used in the simulation. The repeated sampling procedure provided an empirical basis for assessing the approximate normality of the sampling distributions, thereby supporting the application of normal-based statistical methods in the Fixed-Horizon A/B testing framework.

![Figure1](figures/figure1.png)

**Evaluation of Fixed-Horizon A/B Testing Under the Null Hypothesis (A/A Testing)**

To evaluate the statistical validity of the Fixed-Horizon A/B Testing framework, we conducted a simulation study consisting of 1,000 independent A/A testing experiments. In each experiment, both the control and treatment groups were assigned the same underlying CTR  $p_{\text{control}}=p_{\text{treatment}}$, ensuring that no actual treatment effect existed. A fixed sample size of 120,000 observations was considered for each experimental group.

The primary objective of this simulation was to examine the distribution of p-values under the null hypothesis and assess whether the testing procedure maintained the specified False Positive Rate (FPR).

The simulation results indicated that the p-values were approximately uniformly distributed between 0 and 1. Furthermore, the empirical FPR was observed to be approximately 0.05, consistent with the predefined significance level of $\alpha=0.05$. The corresponding cumulative distribution function (CDF) plot exhibited an approximately straight diagonal line, providing further evidence of uniformity in the p-value distribution.

These findings suggest that the Fixed-Horizon A/B Testing framework maintains the nominal Type I Error rate under the null hypothesis and provides statistically reliable results when the experiment is conducted using a predetermined sample size without premature stopping.

![Figure2](figures/figure4.png)

**Evaluation of Statistical Power Under the Alternative Hypothesis (A/B Testing)**

To evaluate the ability of the Fixed-Horizon A/B Testing framework to detect an actual difference between two experimental variants, we conducted a simulation study consisting of 1,000 independent A/B testing experiments under the alternative hypothesis.

In this setting, the control and treatment groups were assigned different underlying CTR values, such that:

$$
H_1:p_{\text{control}}\neq p_{\text{treatment}}
$$

Unlike the A/A testing scenario, where both variants have identical CTRs, this experiment introduces a genuine difference between the two groups to assess the ability of the statistical testing procedure to identify the treatment effect.

The p-values obtained from the 1,000 simulation replications were examined to evaluate the detection capability of the testing framework. Under the alternative hypothesis, the p-value distribution was expected to concentrate towards smaller values, indicating stronger evidence against the null hypothesis.

The simulation results produced an estimated statistical power of approximately 0.85 (85%), which is slightly higher than the predefined target power of 0.80 (80%). This indicates that, for the selected sample size and treatment effect, the Fixed-Horizon testing framework successfully detected the difference between the two experimental variants in approximately 85% of the simulation replications.

Overall, these findings demonstrate that the Fixed-Horizon A/B Testing framework provides satisfactory statistical power while maintaining the nominal 5% False Positive Rate under the null hypothesis.

![Figure6](figures/figure6.png)


**A/A Testing with Early Stopping: Effect of Peeking on False Positive Rate**

To investigate the statistical consequences of repeated monitoring and premature termination, we extended the simulation study by introducing an early-stopping mechanism into the A/A testing framework.

Unlike the conventional Fixed-Horizon approach, where statistical inference is performed only after reaching the predetermined sample size, the early-stopping framework allows repeated examination of experimental results during the data collection process.

For this experiment, we again conducted 1,000 independent A/A testing simulations, maintaining identical underlying CTRs for the control and treatment groups. The peeking frequency was set to 10, meaning that the statistical significance was evaluated at 10 interim analysis points during the experiment.

An early-stopping rule was implemented whereby the experiment was terminated whenever the calculated test statistic crossed the predefined critical significance boundary at any interim analysis. Since both experimental variants had identical underlying CTRs, any statistically significant result represented a false-positive finding.

The simulation results demonstrated a substantial inflation in the False Positive Rate, which increased to approximately 20.1%, compared with the nominal significance level of 5%.

This increase indicates that repeatedly examining intermediate results and stopping the experiment as soon as statistical significance is achieved substantially increases the probability of incorrectly rejecting the null hypothesis.

The findings demonstrate the statistical limitations of applying conventional fixed-horizon significance tests with unadjusted repeated monitoring. Although the original Fixed-Horizon framework maintains the desired Type I Error rate when the predetermined sample size is respected, introducing an unadjusted early-stopping mechanism compromises this statistical validity.

Consequently, these results highlight the importance of employing appropriately designed sequential testing procedures, such as the Sequential Probability Ratio Test (SPRT), to control statistical errors while allowing continuous monitoring and early termination of experiments.

![Figure5](figures/figure5.png)

**Evaluation of False Positive Rate (FPR) Under the Null Hypothesis: SPRT A/A Testing**

To evaluate the statistical validity of SPRT under the null hypothesis, we conducted an A/A testing simulation in which both the control and treatment groups were assigned identical underlying CTR values. Since both variants represented the same underlying population, no actual treatment effect existed.

The SPRT procedure was implemented using an early-stopping mechanism based on predefined likelihood-ratio decision boundaries. As new observations became available, the cumulative SPRT score was recalculated and compared against the upper and lower stopping boundaries.

If the likelihood ratio crossed either boundary, the experiment was terminated and the corresponding statistical decision was recorded. Otherwise, additional observations were collected, and the process continued.

The simulation was performed across 10 independent runs, each consisting of 1,000 replications. The primary objective was to examine whether SPRT could maintain the desired Type I Error probability while allowing early termination of experiments.

The simulation results indicated that the empirical False Positive Rate was approximately 0.045 (4.5%), which was close to the predefined significance level of 0.05 (5%). This suggests that the SPRT procedure maintained an acceptable level of Type I Error under the null hypothesis.

Furthermore, the average sample size required to reach a statistical decision was approximately 22,000 observations per experimental group. 

![Figure8](figures/figure8.png)

**Evaluation of Statistical Power Under the Alternative Hypothesis: SPRT A/B Testing**

To evaluate the ability of the Sequential Probability Ratio Test (SPRT) to detect a genuine difference between two experimental variants, we conducted a simulation study under the alternative hypothesis using an A/B testing framework.

Unlike the A/A testing experiment, in which both groups were assigned identical underlying CTR values, the A/B testing simulation considered two different variants with distinct CTRs for the control and treatment groups. This enabled us to examine the detection capability of SPRT when an actual treatment effect exists.

The experiment was implemented using a sequential monitoring mechanism with predefined likelihood-ratio decision boundaries. As new observations became available, the cumulative SPRT statistic was updated and compared against the upper and lower stopping boundaries. If either boundary was crossed, the experiment was terminated and the corresponding statistical decision was recorded. Otherwise, additional observations were collected until a stopping condition was satisfied.

To obtain reliable estimates of statistical performance, the simulation was conducted over 10 independent runs, with each run consisting of 1,000 simulation replications. The primary objective was to estimate the average statistical power and the average sample size required by SPRT to detect the difference between the two experimental variants.

The simulation results indicated that SPRT achieved an average statistical power of approximately 82.1%, which is slightly higher than the predefined target power of 80%. This suggests that the sequential testing procedure successfully detected the specified treatment effect in approximately 82.1% of the simulated experiments.

Furthermore, the average sample size required to reach a statistical decision was approximately 33,000 observations per experimental group. This indicates that SPRT was able to achieve the desired detection capability while employing sequential monitoring and an early-stopping mechanism.

Overall, the results demonstrate that SPRT achieved satisfactory statistical power under the alternative hypothesis. When considered alongside the A/A testing results, which produced an empirical False Positive Rate of approximately 4.5%, these findings suggest that SPRT maintained an acceptable balance between Type I Error control and the ability to detect genuine treatment effects under the specified simulation conditions.

![Figure9](figures/figure9.png)


### **Conclusion** 

Based on the simulation results, it can be concluded that the Sequential Probability Ratio Test (SPRT) offers a statistically efficient alternative to the conventional Fixed-Horizon A/B Testing framework, particularly in terms of sample-size requirements and testing duration. The findings indicate that SPRT can substantially reduce the number of observations required to reach a statistical decision while maintaining an acceptable level of False Positive Rate (FPR) and statistical power within the predefined experimental parameters.

The simulation analysis further reveals that the sample-size requirements of SPRT depend on the underlying treatment effect. In particular, SPRT requires a different number of observations depending on the extent of the difference between the control and treatment variants. When the experimental evidence is sufficient to distinguish between the two variants, the sequential procedure can terminate the experiment early. Conversely, detecting a genuine treatment effect may require additional observations to accumulate sufficient statistical evidence to cross the predefined decision boundaries.

Overall, the findings suggest that SPRT has considerable potential to improve the efficiency of A/B testing within digital experimentation frameworks, particularly for evaluating Click-Through Rates (CTR). Its ability to continuously monitor experimental outcomes and make decisions based on accumulated statistical evidence makes it a useful alternative to traditional fixed-horizon testing. Therefore, SPRT can help reduce experimentation time and potentially lower the resources required for digital optimization while preserving statistical reliability.

In conclusion, the study demonstrates that sequential testing, particularly SPRT, provides a promising statistical framework for conducting more efficient A/B experiments. Its application can be particularly beneficial in digital analytics environments where large volumes of user impressions and click observations are continuously generated.