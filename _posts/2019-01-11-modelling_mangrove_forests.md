---
layout: post
title:  "Modelling mangrove forests"
author: sal
categories: [ PLS-R, partial least squares, R, PCA, mangroves ]
image: assets/images/mangrove.jpg
featured: true
hidden: false
---

Have you been to a mangrove? 
Mangroves are forests having an identity crisis: 
In case you are wondering, it is actually very difficult to be a terrestrial tree in the marine environment. That's because life (as we know it) is based on water, and fr

Well, unlike tropical or temperate forests, mangroves are rarely studied so there's a lot we don't know about them. 
In 2017 I undertook a one-year long project to fill some gaps, and this is a brief discussion of it's outcomes.

So having so little data available, I was interested 

Can we predict how much biomass a mangrove will produce, if we have basic information on the structure of its trees?
And the Answers is YES! At least is seems to work (you can read the full publication <a href="" ><>, or <a href=""> send me an email<> if you can't.

Why PLS-R? PLS-R is a fantastic tool for anyone dealing with biological data. That's because, with few exceptions, biological features are usually ortogonal (cross-correlated). That hampers, for instance, the use of more common techniques, such as (multivariate) linear regressions. 

Basically, the steps to 
Organize the features dataset (containing the 
Organize the response dataset (observed annual biomass production of each site)
Run the PLS-R 

How can this model be used? Ideally, . Of course, I don't believe we are there yet, because, as I mentioned above, this was the first attempt to Ideally, once a robust model , we could go to a mangrove forest, measure some trees (width and height, density, basal area) and . Is this helpful? YESSS because measuring trees takes a few hours (or maybe a few days, depending on forest size, acessibility, ect.). But estimating the annual biomass production, takes at least a year. So that's why I started looking into this in the firts place: Can we obtain more data more quickly, and use a model to predict Well, I hope . Because science is always auto-correcting itself, and we learn a little bit with every new model, table, dataset, chart that comes around.



 <span class="spoiler">I just love mangroves</span>


