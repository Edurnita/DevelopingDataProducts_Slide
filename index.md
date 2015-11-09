---
title       : The wine example using K-Means (Clustering technique)
author      : Edurne Alonso Morán
framework   : revealjs        
highlighter : highlight.js  
widgets     : []            
mode        : selfcontained 
knit        : slidify::knit2slides
navigation  : slide
---

## The wine example using K-Means (Clustering technique)

Author : Edurne Alonso Moran

---

## Introduction

A dataset containing 13 chemical measurements on <span style="color:green; font-weight:bold">178 Italian wine samples</span> is analyzed. These data are the results of a chemical analysis of wines grown in the same region in Italy but derived from three different cultivars.

--- .class #id

## Methodology

1) For building the shiny app, a <span style="color:green; font-weight:bold">K-means cluster</span> of the data is performed. The number of clusters is determined by user. 

2) Since K-means cluster analysis starts with <span style="color:green; font-weight:bold">k randomly chosen centroids</span>, a different solution can be obtained each time the function is invoked. Indeed, the variables vary in range, so they are <b>standardized</b> prior to clustering.

--- &twocol 

## R code and plot

*** =left
R code

```
## Loading required package: MASS
## This is vegan 2.3-1
```


```r
data(wine)
df<-scale(wine[-1])
c<-kmeans(df,3)
cmd<-cmdscale(dist(df))
groups<-levels(factor(c$cluster))
ordiplot(cmd)
for(i in seq_along(groups)){
  points(cmd[factor(c$cluster)==groups[i],],col=i,pch=16)}
ordispider(cmd,factor(c$cluster),label=TRUE)
ordihull(cmd,factor(c$cluster),lty="dotted")
```

*** =right
R plot
![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 

---

## My Shiny App

The image of the shiny app designed is the following one:

![](assets/img/shinyapp.png)
