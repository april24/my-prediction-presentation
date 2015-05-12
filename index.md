---
title       : Prediction with Galton's Data
subtitle    : Linear Regression Model
author      : RongChen
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]      # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Galton'Data
There are two questions we trying to answer:


1.To try to find a parsimonious, easily described relationship between parent and children's heights.

2.To use the parents' heights to predict children's heights.

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png) 

--- .class #id 

## The solution of the best fit model
Let $Y_i$ be the $i_th$ child's height and $X_i$ be the $i_th$ parents' heights.

Consider finding the best line: $Child's Height = \beta_0+ Parent's Height*\beta_1$

Our goal is to minimize the least squares: $$\sum_{i=1}^n \{Y_i-(\beta_0+\beta_1X_i)\}^2$$

R can help us find the best fit model

```r
fit<-lm(child~parent,data=galton)
```


--- .class #id 

## Visualizing the best fit line 

![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png) 


--- .class #id 

##  Prediction and My Shiny Application


Finally, Here is my application on Rstudio's shiny server
https://april.shinyapps.io/prediction/

Everyone can use it to understand how linear regression model works and predicte childrens' heights via parents' heights.The function I use to predict is as follows:

```r
bestfit<-function(parent_height) {
    fit<-lm(child~parent,data=galton)
    coef(fit)[1]+coef(fit)[2]*parent_height
}
```





