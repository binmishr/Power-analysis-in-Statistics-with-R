# Power-analysis-in-Statistics-with-R

Power analysis in Statistics, there is a probability of committing an error in making a decision about a hypothesis.

Hence two types of errors can occur in hypothesis, Type I error and Type II Error.

The probability of Type I error is denoted as α and the probability of Type II error is β.

Type 1 Error:- p(reject H0/H0 is true)=α

Type II Error:- p(accept H0/H1 is true)=β

We find Type II error is more serious than Type I error. Hence α may be relatively larger than β.

Power Analysis in Statistics

For testing a hypothesis H0 against H1, the test with probabilities α and β of Type I and Type II errors respectively, the quantity (1- β) is called the power of the test.

The power of the test depends upon the difference between the parameter value specified by H0 and the actual value of the parameter.

The level of significance may be defined as the probability of Type I error which is ready to tolerate in making a decision about H0.

The size of a non-randomized test is defined as the size of the critical region. Practically, it is numerically the same as the level of significance.


Power analysis is one of the important aspects of experimental design. It allows us to determine the sample size required to detect an effect of a given size with a given degree of confidence.

And it allows us to determine the probability of detecting an effect of a given size with a given level of confidence, under-sample size constraints.

The power of the test is too low we ignore conclusions arrived from the data set.

In R, the following parameters required to calculate the power analysis

    Sample size
    Effect size
    Significance level
    Power of the test

If we have any of the three parameters given above, we can calculate the fourth one.

Following table provide the power calculations for different types of analysis.
Function	Power Calculation For
pwr.2p.test	two proportions equal n
pwr.2p2n.test	two proportions unequal n
pwr.anova.test	balanced one way anova
pwr.chisq.test	chi square test
pwr.f2.test	general linear model
pwr.p.test	proportion one sample
pwr.r.test	correlation
pwr.t.test	t-tests (one sample, 2 samples, paired)
pwr.r.test	t-test (two samples with unequal n)

The significance level α defaults to be 0.05.

Finding effect size is one of the difficult tasks. Your subject expertise needs to brought to be here. Cohen gives the following guidelines for the social sciences. For more details about effects size you can refer here
Effect size	Cohen’s w
Small	0.10
Medium	0.30
Large	0.50

library(pwr)

For a one-way ANOVA comparing 4 groups, calculate the sample size needed in each group to obtain a power of 0.80, when the effect size is moderate (0.25) and a significance level of 0.05 is employed.

pwr.anova.test(k=4,f=.25,sig.level=.05,power=.8)

Balanced one-way analysis of variance power calculation

              k = 4
              n = 44.59927
              f = 0.25
      sig.level = 0.05
          power = 0.8
NOTE: n is number in each group

What is the power of a one-tailed t-test, with a significance level of 0.05, 12 people in each group, and an effect size equal to 0.75?

pwr.t.test(n=12,d=0.75,sig.level=.05,alternative="greater")

Two-sample t test power calculation

              n = 12
              d = 0.75
      sig.level = 0.05
          power = 0.5538378
    alternative = greater
NOTE: n is number in *each* group

Using a two-tailed test proportions, and assuming a significance level of 0.05 and a common sample size of 20 for each proportion, what effect size can be detected with a power of .75?

pwr.2p.test(n=20,sig.level=0.05,power=0.75)

Difference of proportion power calculation for binomial distribution (arcsine transformation)

              h = 0.8331021
              n = 20
      sig.level = 0.05
          power = 0.75
    alternative = two.sided
NOTE: same sample sizes
