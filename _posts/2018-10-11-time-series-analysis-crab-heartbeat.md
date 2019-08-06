---
layout: post
title:  "time-series analysis of heartbeats"
author: Aline
categories: [ data-science ]
image: assets/images/PB107651.JPG
featured: false
hidden: true
beforetoc: "beforetoc"
toc: true
---


Scientists worldwide record and analyze the heartbeats of all animals you can think of. From the largest to the tiniest. In the same way your doctor can learn a lot from your health by monitoring your hear frequency, scientists investigate the behavior and physiology of animal too.

A couple years ago I collaborated on a project where scientists wanted to see how crabs were being affected by
They used a system called Picoscope to get the crab's heartbeats by attaching small sensors to the crabs' back (_fun fact_ the crab's heart is not located on its "chest" but rather on its "back"). The crabs were then confined to a space where one or more environmental features are being manipulated. In this case, it was the water temperature.

The experiment can be repeated with diferent individuals, different species, under n diferent conditions, depending on what the *research question* is.

Well, after an experiment like this is done, a researcher may end up with hours of recording per individual, and dozens of individuals. Consider that a crab's heart rate is about **per min**, that's a lot
The thing is, the features being manipulated (temperature, gas concentration, light, etc.) are being recorded by their own specific sensors, and the researcher will have to integrate these data at some point.

Enters me. Speaking data-science language, we need to relate the features dataset (temperature) to the response dataset, which are the heartbeats.
After this is doe, we have a dataset of environmental factor vs. heart beat frequency (in hertz) per unit of time (minutes, in our case).

From that on,    
