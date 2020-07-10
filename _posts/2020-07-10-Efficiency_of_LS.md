---
title: "How efficient is the Least squares estimator under perfect conditions?"
author: "Rasmus M. Jensen"
date: "2020-07-10"
layout: post
categories: Research
tags: [computational economics, econometrics]
image: LinearOLSCS1.png # for open graph protocol
---

## Introduction

Being a very simple linear fitting method the ordinary least-squares (OLS) estimator is quite popular, both in time-dimension analysis; time-series analysis and in conventional cross-sectional analysis.
The benefits of the OLS-estimator are many; under the assumption of a linear Gaussian model the estimator holds a analytical solution, which in many cases eases the computational burden associated with estimation and inference.
Secondly, under linear Gaussianity the analytical solution coincides with the maximum likelihood solution. This implies in turn that no other (paramatric) estimator are better than the OLS-estimator.
Lastly, the estimator is known and utilized throughout all of academia, implying that, except in very scarce (and specific) cases, no editor is going to question the usage of the OLS-estimator.

But really how good is the OLS-estimator given the optimum of conditions? To explore this area, and to improve my [Shiny skills](https://shiny.rstudio.com), I set out to write an app that explores the OLS-estimator in both the cross-sectional and the time-series dimension using a Monte-Carlo approach.

## The App
[The app](https://rasmusjensen96.shinyapps.io/LeastSquaresEfficiency/) relies only on native (base) R-features and ggplot. The main-panel consists of two dynamic graphs.
Firstly, a benchmark simulated data-set (the size of which is customizable by the user). If the user chooses the "Time-dimension" option, the simulated data consists of an autoregressive model of order 1 (AR(1)):

$$ y_t = \beta y_{t-1} + \epsilon_t, \qquad \epsilon_t \sim \mathcal{N}\left( 0,1\right) $$

The correlation coefficient $$\beta$$ can be chosen by the user freely on the space spanning $$\left[-1;1\right]$$, in the time-dimension the AR(1) has a special case when $$\beta$$ is on the unit-circle (in our case -1 or 1), then the model is referred to as a random walk. In this case the OLS-estimator holds some undesirable properties.
Should the user instead opt for the "Cross-sectional"-option the model is a simple bivariate linear regression on the form:

$$ y_i = \beta x_i + \epsilon_i \qquad \epsilon_i \sim \mathcal{N}\left( 0,\sigma\right) $$

In this case I added an option to reduce or increase the noise through the slider for $$\sigma$$. Reducing the error-standard deviation to 0 results in a perfect linear relationship between $$x$$ and $$y$$ and thus an $$R^2$$-value (coefficient of determination) of 1. On the other hand increasing the magnitude of the noise, decreases the $$R^2$$-value indefinitely (equivalent to decreasing the signal-to-noise ratio).

The second panel shows a histogram and a kernel-density plot (probability-distribution approximation) of a Monte-Carlo simulation of a user-specified number of random simulations. For very small Monte-Carlo samples the density is poorly behaving, increasing the number of MC-replications it is evident the the Central Limit Theorem and Law of Large numbers works its magic. The mean of the approximate PDF is close to the true mean with the characteristic normal-bell shape around the mean (as it should). Increasing the sample size (N) further increases the precision of the slope estimates. 

## Some graphs


