---
layout: post
title:  "Predicting the effects of global warming on the mountains of Austria"
author: Aline
categories: [ ecology, data-science ]
image: assets/images/mountains-austria.jpg
featured: false
hidden: false
beforetoc: "Temperate mountains hold precious stocks of organic carbon. "
toc: true
---


Our experimental design was like this

5 mountains to replicate the study
2 sites per mountain (diferent altitudes)
5 blocks of mesocosms per site
4 mesocosms per block

This is a classic example of __nested data__ (mesocosms belong to blocks, which belong to sites, which belong to mountains...). Experiments like this are necessary to isolate (or to account for) the effects of other variables that might influence the results. So, in our case,

To analyse this data, I used a __mixed effect model__. Mixed effect models (that's why the "mixed") quantify the effects of the desired treatments (*fixed effects*) while taking into account the variation that is due to the influence of other, unknown factors (*random effects*).

Here's how to run a __mixed effect model__ in R:

```

```
