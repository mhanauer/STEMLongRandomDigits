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
Now we are going to combine the id values with some sample test to test the system.
```{r}
dataTest =read.csv("LongSTEMInvite.csv", header = TRUE, na.strings = TRUE)
# Remember that for qualtrics need to delete the first two lines of code
dataTest = dataTest[-c(1:2), ]
dataTest = as.data.frame(dataTest)
# Just keeping Q1, because that is the email question
dataTest = dataTest[c("Q1")]
# With the actual data just use the data set above.  But since I only have two users for this example, I am just making up the ids.
ID = c(1234,4321)
dataTest = cbind(ID, dataTest)
names(dataTest) = c("ID", "Email")
write.csv(dataTest, "dataTest.csv", row.names = FALSE)
```

