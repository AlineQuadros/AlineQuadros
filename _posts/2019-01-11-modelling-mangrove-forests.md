---
layout: post
title:  "Modelling the production of mangrove forests with PLS-R and PCA"
author: Aline
categories: [ mangroves, data-science, ecology ]
image: assets/images/mangrovesfranciscoblancosstock.jpg
featured: true
hidden: false
beforetoc: "How a combination of PLS-R and PCA helped me to predict how biomass production might change depending on the vegetation features"
toc: false
---

> Photo credits: Francisco Blanco

Mangroves are fascinating coastal ecosystems, that harbor

Well, unlike tropical or temperate forests, mangroves are not well studied so there's a lot we don't know about them. In 2017 I undertook a one-year long project to fill some gaps, and this post has a brief discussion of one of it's outcomes.

Initially, my task was to review published and unpublished papers (basically, a manual text-mining, you can read more about it <a href="https://alinequadros.github.io/AlineQuadros/playing-data-detective/">in this post</a>) and extract this information to

>__Traits__ are quantitative and qualitative features of living beings that help biologists to model the ecology, behavior, and are extremely useful in **quantitative ecology** these days.

While I was doing the reviews, I found two interesting sets of studies. One set contained studies about the **vegetation structure** of mangrove stands (tree height, diameter, density, etc), and another set had estimates of their annual litterfall production. Some studies even contained both information (the list of studies is at the end of this post).

Well, . Litterfall is a big component (and a proxy) of the annual aboveground
<img src="/AlineQuadros/assets/images/mangrove_npp.png">
> Mangroves store huge amounts of carbon in the sediments. This is so special in terms of global ecology that it <a href="https://en.wikipedia.org/wiki/Blue_carbon">Blue Carbon</a>. Much of this carbon comes from the freshwater inflow from rivers, but a lot comes from the decomposition of the leaves shed by the trees everyday, __the leaf litterfall__. 


Could we predict how much biomass a mangrove will produce, if we have basic information on the structure of its trees?
And __the answer is YES!__ At least is seems to work (you can read the full publication <a href="https://doi.org/10.1016/j.ecss.2018.12.012">here</a>, or <a href=""> send me an email</a> if you don't have access to it.

Why did I choose to use PLS-R? Well PLS-R is a fantastic tool for anyone dealing with biological data. That's because, with few exceptions, biological features are usually orthogonal (cross-correlated). That hampers, for instance, the use of more common techniques, such as (multivariate) linear regressions. If PLS is completely new to you (as it was new to me before this project) let me tell you I learned a lot about it by reading Gaston Sanchez's <a href="https://sagaofpls.github.io/"> The Saga of PLS </a>.

Basically, the steps to apply a PLS-R to your data are:

1) Organize the features dataset (containing the
2) Organize the response dataset (PLS-R in <a href="https://github.com/gastonstat/plsdepot">package plsdepot</a> can handle univariate and multivariate responses)
3) Apply normalization to your data, since biological traits come in a variety of scales (cm, ind/m2, mm, counts, etc.)
4) Run the PLS-R with cross-validation

Here's some useful functions to run the analysis with <a href="https://github.com/gastonstat/plsdepot">plsdepot</a> for R:
```
library(plsdepot)


X = dataset[predictor_vars]   # set predictors/features
y = labels                    # set the response variable

# fit the model
pls1_model <- plsreg1(X, Y)

# inspect the results
pls1_model$R2          # Vector of PLS R-squared
pls1_model$cor.xyt     # Correlations between the variables and the PLS components
pls1_model$reg.coefs   # Vector of regression coefficients (used with the original data scale)
pls1_model$Q2          # Table with the cross validation results.

# calculate the Variable Importance - useful for interpretability of the model

library(PLSbiplot1)
mod.VIP(X=X, Y=y, algorithm=mod.SIMPLS, A=2, cutoff=1)

# plot
plot(pls1_model)
```


Once the model is obtained, we can **predict** the litterfall production of new sites that contain these two species. Because I didn't have additional data to use with my models, I created a set of **artificial data** to experiment with my models.

```
# Run a PCA with the same predictor variables used in the PLS-r
pca1<- prcomp(X, center = TRUE, scale = TRUE, retx=TRUE)
biplot(pca1,  xlim=c(-0.8, 0.8), ylim=c(-0.8, 0.8))
summary(pca1)


```

Finally

```
#sim_sites.med
sim_sites.mean <- apply(sites_for_sim, 2, mean,  na.rm = TRUE)
sim_sites.cov <- cov(sites_for_sim, method="pearson")


#Make new random data based on the calculated biometry info. each species
#The MASS package allows for the calculation of correlated/covarying random
#numbers using this information.
require(MASS)
set.seed(1)
#simulate  sites
n <- 5000

new.sites_sim <- mvrnorm(n, sim_sites.mean, sim_sites.cov, empirical=TRUE)
```

How can this model be used? Ideally, we could visit a few mangrove stands, collect data from a few trees (species ID, height, diameter), and collect data about how the trees are distributed within each stand (density and basal area). Feeding this data into the model, __we could predict how much biomass this stand will produce in a year__


But is this helpful? YESSS because measuring, identifying , and counting trees takes a few hours or a few days (depending on forest size, accessibility, etc.). But estimating the annual biomass production takes __at least an year__. And understanding biomass production is crucial  So that's why I started looking into this in the first place: Can we obtain more data more quickly, and use a model to predict Well, I hope . Because science is always auto-correcting itself, and we learn a little bit with every new model, table, dataset, chart that comes around.

We might not be there yet, because, as I mentioned above, this was the first attempt to. Ideally, once a robust model is stablished, and the coefficients for more species, we could go to a mangrove forest, measure some trees (width and height, density, basal area) and predict how much .


 <span class="spoiler">Thank you for reading it</span>
