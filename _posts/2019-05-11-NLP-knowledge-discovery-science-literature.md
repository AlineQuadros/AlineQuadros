---
layout: post
title:  "Using NLP and d"
author: Aline
categories: [ NLP, data-science ]
image: assets/images/mangrove.jpg
featured: true
hidden: true
beforetoc: "NLP is finally giving scientists the possibility to connect precious information that is scattered over hundreds of  publications"
toc: true
---

I am absolutely **in love with NLP**, and I'm excited to see how this field is progressing fast.
Being a scientist,

This small project was my first attempt to explore NLP and see how much knowledge I could
Because I was working on the Mangrove Ecology at the time, it was natural to try to apply this technique to understand more of mangroves. Nonetheless, the procedures I'll describe below can be used to investigate many other subjects.

The question was simple:

> What aspects of mangrove ecology have been studied and how has it changed over the years?

* First step was getting the data. My sources where three major databases of scientific literature: **PubMED**, **Web of knowledge**, and **Scopus**. Why was it necessary to use three databases? Well, each database indexes a diferent set of journals and publishers, so even if you use the exact same keywords you'll get a diferent set of publications. There's a lot of overlap, yes, but  using a combination of keywords, I obtained the titles and abstracts

* Second step, you know, data wrangling: identification of duplicates, normalization of charsets, . The final dataset looks like this:

> The oldest publication about mangrove *ecology* that I could find was ...

* Third step: build a corpora (including text normalization, stemming)

* Fourth step is _Where the fun starts_: Find out the most common used word in the titles.
Because I had the publication year of each publication (I grouped them per decade), I was able to detect trends . I assumed that this list would provide a good overview of how the interest on mangroves has been changing along time. The results look like this:



> Disclaimer: I only analysed publications in English, which is a pitty. Most mangroves of the world occur in non-English speaking  countries (like Brazil ), so there's a lot published in the researcher's country language





 <span class="spoiler">I just love NLP</span>
