# An Accurate Implementation of the Studentized Range Distribution for Python

By Samuel Wallan, Dominic Chmiel, and Matt Haberland

## Introduction

As data becomes more and more accessible in a world awash with computers, it can be tempting follow a practice called "p-hacking", or misusing data analysis in order to show an artificially  significant statistical corellation. For example, there appears to be a correllation between the number of letters in the Scripps National Spelling Bee and the number of people killed by venomous spiders in the United States every year. Several carefully designed statistical tests that gaurd against this practice rely on the studentized range distrbution by accounting for the number of comparisons in their statistic and p-value. One such test is Tukey's HSD (Honest Significant Difference) test, which utilizes the studentized range distribution's Percent Point Function (PPF), to measure the range of data from a normally distributed sample.

Precomputed tables exist for the studentized range distrbution, but can only approximate results should input data not fall within the tables' bounds. However, the probability distribution function (PDF) and cumulative distribution function (CDF) for the studentized range are computationally challenging to evaluate due to their complicated double integrals. The PPF is the inverse of the CDF. Therefore, in this paper we present a pythonic, fast, accurate, and direct implementation of the studentized range distribution for SciPy in addition to tests that demonstrate its accuracy and performance. 

## The Distribution
The studentized range's PDF and CDF take the following forms, respectively [1]:


![image](https://i.ibb.co/VDPQDxx/Screen-Shot-2021-07-11-at-9-25-33-PM.png)

where \phi(z) and \Phi(z) represent the normal PDF and normal CDF, respectively.

## Implementations

### A Very Direct Implementation

To establish a baseline, we evaluate the CDF exactly as written in equation (2), using nested calls to SciPy's `integrate.quad` to evaluate the double integral.


[Check out the full notebook ](https://colab.research.google.com/drive/12WsuDWyZpdcBR0Dk7qpzFKAZkEY3IgwU?usp=sharing) to see more.
