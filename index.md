---
title       : Developing Data Products
subtitle    : Shiny Application and Reproducible Pitch
author      : Kelvin Lim
job         : Student
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Project Requirement

Your Shiny Application

1. Write a shiny application with associated supporting documentation. The documentation should be thought of as whatever a user will need to get started using your application.
2. Deploy the application on Rstudio's shiny server
3. Share the application link by pasting it into the text box below
4. Share your server.R and ui.R code on github

The application must include the following:

1. Some form of input (widget: textbox, radio button, checkbox, ...)
2. Some operation on the ui input in sever.R
3. Some reactive output displayed as a result of server calculations
4. You must also include enough documentation so that a novice user could use your application.
5. The documentation should be at the Shiny website itself. Do not post to an external link.

The Shiny application in question is entirely up to you. However, if you're having trouble coming up with ideas, you could start from the simple prediction algorithm done in class and build a new algorithm on one of the R datasets packages. Please make the package simple for the end user, so that they don't need a lot of your prerequisite knowledge to evaluate your application. You should emphasize a simple project given the short time frame.  

--- .class #id 

## Dataset Used

ChickWeight {datasets}

Description
The ChickWeight data frame has 578 rows and 4 columns from an experiment on the effect of diet on early growth of chicks. The body weights of the chicks were measured at birth and every second day thereafter until day 20. They were also measured on day 21. There were four groups on chicks on different protein diets.

weight
a numeric vector giving the body weight of the chick (gm).

Time
a numeric vector giving the number of days since birth when the measurement was made.

Diet
a factor with levels 1, ..., 4 indicating which experimental diet the chick received.

(Chick
an ordered factor with levels 18 < ... < 48 giving a unique identifier for the chick. The ordering of the levels groups chicks on the same diet together and orders them according to their final weight (lightest to heaviest) within diet.)

---

## Widgets used in the application

Shiny application: Output - This application will allow a person to find out the average weight of a chick given a certain diet and age.

Radiobutton - A radio button field to select the diet which the check received. ("1","2", 
"3","4")

FieldInput - To key in the Time aka age of the chick (0-21)

---

## Application link and code repository

Application is on the RStudio shinyapps.io website: http://weibin-kelvin.shinyapps.io/APP2

Code is on github website: https://github.com/weibin-kelvin/DDP_Project

---

## Calculation


```r
fx <- function(x,y) {
  
  data <- ChickWeight
  z <- data[data$Diet == x   , ]  
  z <- data[data$Diet == x &
                data$Time == y, ]
  out <- mean(z$weight)
  return (out)
}

fx(2,10)
```

```
## [1] 108.5
```

---
