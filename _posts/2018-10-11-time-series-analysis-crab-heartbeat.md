---
layout: post
title:  "Analysis of crab heartbeats using LOESS for curve smoothing and peak detection"
author: Aline
categories: [ data-science ]
image: assets/images/crab-tree.jpg
featured: false
hidden: false
beforetoc: "beforetoc"
toc: true
---


Scientists worldwide record and analyze the heartbeats of all animals you can think of. From the largest to the tiniest. In the same way your doctor can learn a lot from your health by monitoring your hear frequency, scientists investigate the behavior and physiology of animal too.

A couple years ago I collaborated on a project where scientists wanted to see how crabs were being affected by global warming. They used a system that records the heartbeats by an infra-red sensor attached to the crabs’ carapace connected to an oscilloscope. ) to get the crab's heartbeats by attaching small sensors to the crabs' back (_fun fact_ the crab's heart is not located on its "chest" but rather on its "back"). The crabs were then confined to a space where one or more environmental features are being manipulated. In this case, it was the water temperature.

<img src='/AlineQuadros/assets/images/signal1.png'>  

> Heart frequency is one of the most important physiological . Through the analysis of heartbeats, scientists can understand which conditions bring stress to animals, and how much of each stress the can support until reaching a critical condition. This information is latter used to predict how different species will respond to environmental changes, such as global warming.  

The experiment can be repeated with diferent individuals, different species, under diferent conditions, depending on the *research question*.

Devices such as Picoscope convert the analogical signal coming from the animal and convert it to a digital form that can be saved in text files and analyzed. Well, after an experiment like this is done, a researcher may end up with dozens hours of recordings per individual, and dozens of individuals. Consider that a crab's heart rate is about **per min**, that's a lot

<img src='/AlineQuadros/assets/images/signal2.png'>


>The top shows the raw signal (gray lines) and the curves (red) and peaks (green dots) detected using LOESS (local non-parametric regression). From there, we calculate the number of peaks per unit of time (beat per minute, per example), and this series of data is then plotted against the variation of another factor (water temperature, for instance). 

The thing is, the features being manipulated (temperature, gas concentration, light, etc.) are being recorded by their own specific sensors, and the researcher will have to integrate these data at some point.

Enters me. Speaking data-science language, we need to relate the features dataset (temperature) to the response dataset, which are the heartbeats.
After this is done, we have a dataset of environmental factor vs. heart beat frequency (in hertz) per unit of time (minutes, in our case).

```
Time	Channel A	Channel B
(s)	(V)	(V)

0.000000	-0.4205451	0.1358074
0.001334	-0.4652547	0.1329081
0.002668	-0.5101169	0.1301614
0.004002	-0.5548265	0.1274148
0.005336	-0.5548265	0.1245155
0.006675	-0.5548265	0.1217689
0.008004	-0.5548265	0.1190222
0.009338	-0.5996887	0.1161229

```
From that on,    


```
y.loess <- loess(y ~ x, span=0.01, data.frame(x=tmp$time_s, y=tmp$channela))
 y.predict <- predict(y.loess, data.frame(x=tmp$time_s))
 mat2 <- data.frame(tmp$time_s,y.predict)
 # find valleys
 b<- findValleys(y.predict)
 piks <- mat2[b, ]
 piks <- piks[piks$y.predict <=0,]
```




This project has lots of interesting findings, and the partial results were presented in November 2018 by the author of the study, **Pedro Jimenez**, and can be read <a href="/AlineQuadros/assets/images/study_pedro.pdf"> here</a>. There's more coming up!
