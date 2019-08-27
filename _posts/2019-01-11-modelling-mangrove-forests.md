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

Initially, my task was to review published and unpublished papers (basically, a manual text-mining, you can read more about it <a href="playing-data-detective">in this post</a>) and extract this information to

>__Traits__ are quantitative and qualitative features of living beings that help biologists to model the ecology, behavior, and are extremely useful in **quantitative ecology** these days.

While I was doing the reviews, I found two interesting sets of studies. One set contained studies about the **vegetation structure** of mangrove stands (tree height, diameter, density, etc), and another set had estimates of their annual litterfall production. Some studies even contained both information (the list of studies is at the end of this post).

Well, . Litterfall is a big component (and a proxy) of the annual aboveground


Could we predict how much biomass a mangrove will produce, if we have basic information on the structure of its trees?
And __the answer is YES!__ At least is seems to work (you can read the full publication <a href="https://doi.org/10.1016/j.ecss.2018.12.012">here</a>, or <a href=""> send me an email</a> if you don't have access to it.

Why did I choose to use PLS-R? Well PLS-R is a fantastic tool for anyone dealing with biological data. That's because, with few exceptions, biological features are usually orthogonal (cross-correlated). That hampers, for instance, the use of more common techniques, such as (multivariate) linear regressions.

Basically, the steps to apply a PLS-R to your data are the following (using R):
```
library(plsdepot)
library(PLSbiplot1)
library(psych)
library(plsRglm)

X = dataset[predictor_vars]
y = labels # response variable
# fit the 
pls1_avi_1 <- plsreg1(X, Y, comps = 2)
pls1_avi_1$R2
pls1_avi_1$cor.xyt
pls1_avi_1$reg.coefs
pls1_avi_1$Q2
mod.VIP(X=X, Y=Y, algorithm=mod.SIMPLS, A=2, cutoff=1)
```
Organize the features dataset (containing the
Organize the response dataset (observed annual biomass production of each site)
Run the PLS-R
Once the model is obtained, we can **predict**. Because I didn't have additional data to use with my models, I created a set of **artificial data** .

How can this model be used? Ideally, we could visit a few mangrove stands, collect data from a few trees (species ID, height, diameter), and collect data about how the trees are distributed within each stand (density and basal area). Feeding this data into the model, __we could predict how much biomass this stand will produce in a year__


But is this helpful? YESSS because measuring, identifying , and counting trees takes a few hours or a few days (depending on forest size, accessibility, etc.). But estimating the annual biomass production takes __at least an year__. And understanding biomass production is crucial  So that's why I started looking into this in the first place: Can we obtain more data more quickly, and use a model to predict Well, I hope . Because science is always auto-correcting itself, and we learn a little bit with every new model, table, dataset, chart that comes around.

We might not be there yet, because, as I mentioned above, this was the first attempt to. Ideally, once a robust model is stablished, and the coefficients for more species, we could go to a mangrove forest, measure some trees (width and height, density, basal area) and predict how much .

Here are the cool things we can do

If we know a mangrove forest is being cut down, we can predict


Info.


 <span class="spoiler">I just love mangroves</span>
