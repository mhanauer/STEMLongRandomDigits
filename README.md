---
title: "Assign people random numbers"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


```{r}
set.seed(123)
digits = c(1000:9999)
randomDigit =replicate(120,sample(digits, 1, replace = FALSE))
randomDigit = as.data.frame(randomDigit)
id = 1:nrow(randomDigit)
randomDigit = as.data.frame(randomDigit)
randomDigit = data.frame(id = id, randomDigit)
randomDigit
# Removes duplicates, so if there were duplicates we could get rid of them.
dim(randomDigit)
dim(unique(randomDigit))

write.csv(randomDigit, "randomDigit.csv")
```
I need a unique id for each column.  I need the data in long form.  
