---
title: "Publications"
permalink: /mathdoc/
author_profile: true
mathjax: true
---

This page is an explanation of the mathematical models that are used in the tool. 


<b>Data</b>

We assume the availability of a set of samples (possibly noisy) of historical incidents, which we refer to as $D$, and can be represented as a vector of tuples $\\{(s_1,t_1,k_1,w_1),(s_2,t_2,k_2,w_2),\dots,(s_n,t_n,k_n,w_n)\\}$, where $s_i$, $t_i$ and $k_i$ denote the location, time of occurrence, and reported severity of the $i$th incident, respectively, and $w \in \mathbb{R}^m$ represents a vector of features associated with the incident. These features can be spatial, temporal, or spatio-temporal. The features capture covariates that potentially affect incident occurrence. For example, $w$ typically includes features such as weather, population density, and time of the day. The most general form of incident prediction can then be stated as learning a function $f(X \mid w,\theta)$, where the random variable $X$ represents a measure of incident occurrence, and $\theta \in \mathbb{R}^m$ denotes the model parameters. For example, $X$ can measure the \textit{count} of incidents (the number of incidents in $S$ during a specific time period), or \textit{time} between successive incidents. The decision-maker seeks to find the \textit{optimal} parameters $\theta^*$ that best describe $D$. This can be formulated as a maximum likelihood estimation (MLE) problem or an equivalent empirical risk minimization (ERM) problem.


<b>Forecasting</b>

The following forecasting models are currently supported by StatResp --

<ul>
<li><b>Poisson Regression</b>: In Poisson regression, the random variable of interest is the \textit{count} of incidents in a region in a given time frame. The count follows a Poisson distribution, such that 
        
    $$
        f(X= x) = \frac{\lambda^x e^{-\lambda}}{x!}
    $$
    where $\lambda$ is the mean of the distribution. The regression model assumes that the expected value of the mean, conditional on the set of features $w$ can be modeled as 
    
    $$
        \mathbb{E}(\lambda|w) = e^{\sum_{i=1}^{m} \theta_i w_i}
    $$
    
    where $\theta \in \mathbb{R}^m$ is the set of regression coefficients.