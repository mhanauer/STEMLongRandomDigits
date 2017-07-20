---
title: "Assign people random numbers"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

Need a simple example to check and then need to collpase and then can check using excel   

Now need to get rid of the commas
```{r}
set.seed(123)
digits = c(1:5)
randomDigit =replicate(120,sample(digits, 5, replace = FALSE))
id = rep(1,5)
randomDigit = as.data.frame(randomDigit)
randomDigit = data.frame(id = id, randomDigit)
t(randomDigit)
require(dplyr)

randomDigit = randomDigit %>%
  group_by(id) %>%
  summarise_each(funs(toString))

# Removes duplicates, so if there were duplicates we could get rid of them.
dim(randomDigit)
dim(unique(randomDigit))

?unique.data.frame

write.csv(randomDigit, "randomDigit.csv")
```

