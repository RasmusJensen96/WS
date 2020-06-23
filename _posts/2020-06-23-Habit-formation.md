---
layout: post
title: "Predictability of returns under habit-formation"
author: "Rasmus M. Jensen"
categories: documentation
tags: [Finance, computational economics]
image: cuba-1.jpg
---
## Additional content
[MatLab replication tools](https://github.com/RasmusJensen96/Habit-Models-Advanced-Asset-Pricing): Replication guide available in the Readme of the repository.

## Hypothesis
Empirical findings suggest that predictability of financial returns differs through business cycles; high predictability under recessions, low during expansions. Can we replicate this empirical finding in a structural asset pricing model?

## Executional strategy
Setup and estimate a structural consumption-based asset pricing model. Simulate a large number of stock/bond returns under different states of the economy. Examine the properties of the simulated returns and compare them to returns of an empirical market portfolio.

## Model of choice
External habit model of Campbell & Cochrane 1999. Intuition of this model:
  - Model agents (people in the model), chooses their consumption relative to "usual" consumption, i.e. they are driven by habits.
  - Implies: The marginal utility derived from consumption today are negatively affected by the level of consumption yesterday.
In usual models: Utility affected only by absolute and not relative consumption.

A bit more mathematical intuition of the model:\n
$$ U(C_t, X_t) = \mathbb{E}\sum_{t=0}^{\infty}\delta^t \frac{(C_t-X_t)^{1-\gamma}-1}{1-\gamma}$$\n
The utility of the simulated person is given by a utility function $$U_t$$, the variables entering the utility function are consumption $$C_t$$ and a habit-level $$X_t$$. The parameters of the utility function are a subjective discount factor $$\delta$$ (how much does the agent penalize future consumption), and a parameter of relative risk-aversion $$\gamma$$.\n
\n
For a technical walkthrough of the model I refer to the paper.\n
\n
The model parameters are calibrated using US data spanning 1950-2018.

## Results
100,000 (8,332) months (years) worth of stock returns are simulated. Recessions are defined as "low" consumption relative to the habit-level, that is a slow growth of consumption. Three different "low" thresholds are defined as:
    1. Steady state of the model (lower than 6.7% consumption growth)
    2. Matching the empirical and model-implied recession-duration (less than 4.2% percentage growth in consumption)
    3. Extreme situation (less than 2% growth in consumption)
![Histogram of surplus consumption](~/assets/img/DistributionS_t.eps)




### Portfolio Jekyll Theme

This is a Jekyll theme built using the [DevTips Starter Kit](http://devtipsstarterkit.com/) as a foundation for starting, and following closely the amazing tutorial by [Travis Neilson over at DevTips](https://www.youtube.com/watch?v=T6jKLsxbFg4&list=PL0CB3OvPhDA_STygmp3sDenx3UpdOMk7P). The purpose of this theme is to provide a clean and simple website for your portfolio. Emphasis is placed on your projects, which are shown front and center on the home page.

Everything that you will ever need to know about this Jekyll theme is included in [the repository](https://github.com/LeNPaul/portfolio-jekyll-theme), which you can also find in [the demo site](https://lenpaul.github.io/portfolio-jekyll-theme/).

### Jekyll Starter Kit

The Jekyll Starter Kit is a simple framework for starting your own Jekyll project using all of the best practices that I learned from building my other Jekyll themes.

Feel free to check out <a href="https://github.com/LeNPaul/jekyll-starter-kit" target="_blank">the GitHub repository</a>, where you’ll also find instructions on how to use install and use the theme.
