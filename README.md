# ANA-515-Assignment-2
---
title: "ANA 515 Assignment 2"
author: "Mahsa Karkhaneh"
date: '2022'
output: word_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
library(tidyverse)
library(knitr)
library(bslib)
library(dplyr)
library(ggplot2)
```

We have data about cases where police have killed Americans in 2015. This 
contains entries from Guardian's database on police killings and census data from american community survey.
regarding studying of this data set, we can conclude how many percents of these victims are white or not white?
also which city has the most rate of police killing? what is the gender of the majority? this data set has been saved in format CVS.
the Delimiter is ",".

```{r police_killing , echo=TRUE}
url <- "https://raw.githubusercontent.com/fivethirtyeight/data/master/police-killings/police_killings.csv"
police_killing <- read_csv(url)
police_killing<- as.data.frame(police_killing)
# I used read_csv() and as.data.frame() in order to read and consider data set as a data frame to R, respectively. 
```

```{r, echo=TRUE}
#subsetting
mydata <-  police_killing %>% 
  select(name,age,gender,raceethnicity,city,state,pop,h_income,county_income)
#filtering
white <- mydata %>% 
  filter(raceethnicity == "White")
#arrange 
ordered <-arrange(white, age)
#rename column
rename(ordered, white_nwhite=raceethnicity)
```

This data set has `r nrow(mydata)` rows and `r ncol(mydata)` columns.
.The names of the columns and a brief description are in the table below:

``` {r, echo = TRUE}
text_tbl <- data.frame(Names=c("name","age","gender","raceethnicity","city","state","pop","h_income","county_income"),Description=c("Name of deceased","Age of deceased","Gender of deceased","Race/ethnicity of deceased","City where incident occurred","State where incident occurred","Tract population","Tract-level median household income","County-level median household income"))
text_tbl

```

```{r, include=TRUE}
pick3 <- select(police_killing,h_income,county_income,pop)
summary(pick3)

```
[New Text Document.txt](https://github.com/MahsaKarkhaneh/ANA-515-Assignment-2/files/9595781/New.Text.Document.txt)
