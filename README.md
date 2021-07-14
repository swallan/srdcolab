# An Accurate Implementation of the Studentized Range Distribution for Python

By Samuel Wallan, Dominic Chmiel, and Matt Haberland

## Introduction

In a world awash with data and computers, it is tempting to automate the process of scientific discovery by performing comparisons between many pairs of variables in hope of finding correlations. When frequentist hypothesis tests between pairs of variables are performed at a fixed confidence level, increasing the number of tests increases the probability of observing a "statistically significant" result even when the null hypothesis is actually true. Carefully designed tests, such as Tukey's HSD (Honestly Significant Difference) test, protect against this practice of "data dredging", producing p-values and confidence intervals that correctly account for the number of comparisons performed. Several such tests rely on the studentized range distribution, which models the range (i.e. the difference between the maximum and minimum values) of the means of samples from a normally distributed population. Although there are already implementations of these tests available in the scientific Python ecosystem, all of them rely on approximations of the studentized range distribution, which may not be accurate outside the range of inputs for which they are designed. We present the implementation of a reasonably fast and very accurate implementation of the studentized range distribution for SciPy, and we give evidence of its accuracy and performance.

## The Distribution
The studentized range's PDF and CDF take the following forms, respectively [1]:


![image](https://i.ibb.co/VDPQDxx/Screen-Shot-2021-07-11-at-9-25-33-PM.png)

where \phi(z) and \Phi(z) represent the normal PDF and normal CDF, respectively.

## Implementations

### A Very Direct Implementation

To establish a baseline, we evaluate the CDF exactly as written in equation (2), using nested calls to SciPy's `integrate.quad` to evaluate the double integral.


[Check out the full notebook ](https://colab.research.google.com/drive/12WsuDWyZpdcBR0Dk7qpzFKAZkEY3IgwU?usp=sharing) to see more.
