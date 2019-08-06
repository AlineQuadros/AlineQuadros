---
layout: post
title:  "Modelling the biomass production of mangrove forests"
author: Aline
categories: [ mangroves, data-science, ecology ]
image: assets/images/mangrovesfranciscoblancosstock.jpg
featured: true
hidden: true
beforetoc: "How a combination of PLS-R and PCA helped me to predict how biomass production might change depending on the vegetation features"
toc: true
---

> Photo credits: Francisco Blanco

Have you been to a mangrove?
Mangroves are forests having an identity crisis:
In case you are wondering, it is actually very difficult to be a terrestrial plant in the marine environment. That's because life (as we know it) is based on water, and fr

Well, unlike tropical or temperate forests, mangroves are rarely studied so there's a lot we don't know about them.
In 2017 I undertook a one-year long project to fill some gaps, and this post has a brief discussion of one of it's outcomes.

So having so little data available, I was interested

Could we predict how much biomass a mangrove will produce, if we have basic information on the structure of its trees?
And the Answers is YES! At least is seems to work (you can read the full publication <a href="https://www.sciencedirect.com/science/article/pii/S0272771418304426?dgcid=author">here</a>, or <a href=""> send me an email</a> if you can't.

Why did I choose to use PLS-R? PLS-R is a fantastic tool for anyone dealing with biological data. That's because, with few exceptions, biological features are usually ortogonal (cross-correlated). That hampers, for instance, the use of more common techniques, such as (multivariate) linear regressions.

Basically, the steps to
Organize the features dataset (containing the
Organize the response dataset (observed annual biomass production of each site)
Run the PLS-R

How can this model be used? Ideally, . We might not be there yet, because, as I mentioned above, this was the first attempt to Ideally, once a robust model is stablished, we could go to a mangrove forest, measure some trees (width and height, density, basal area) and predict how much .

But is this helpful? YESSS because measuring trees takes a few hours or a few days (depending on forest size, acessibility, ect.). But estimating the annual biomass production, takes at least a year. And understanding biomass production is crucial  So that's why I started looking into this in the first place: Can we obtain more data more quickly, and use a model to predict Well, I hope . Because science is always auto-correcting itself, and we learn a little bit with every new model, table, dataset, chart that comes around.

Here are the cool things we can do

If we know a mangrove forest is being cut down, we can predict


Info.


 <span class="spoiler">I just love mangroves</span>
