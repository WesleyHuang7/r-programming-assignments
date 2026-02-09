Name: Wesley Huang  
Course: LIS4370  

Description:  
This repository contains my R programming assignments and coursework for LIS4370. It will be used to store code, exercises, and related materials as I learn the fundamentals of R and data analysis.

## Blog
Module 2 Blog Post: https://wesleyhuang7.wixsite.com/r-programming-journa

## Module 2 – myMean Function

### Test Result (Original Function)

When I ran `myMean(assignment2)` using the original function, I received the following error:

Error in myMean(assignment2) : object 'assignment' not found

### Why the Function Failed

The function argument is named `assignment2`, but inside the function body it uses variables named `assignment` and `someData`, which do not exist. Because R requires exact variable names, it returns an “object not found” error instead of calculating the mean.

### Corrected Function

```r
myMean <- function(x) {
  sum(x) / length(x)
}

## Correct Output

Running myMean(assignment2) returned:

[1] 19.25


## Module 3 – Poll Data Analysis

This module analyzes a fictional dataset comparing ABC and CBS poll results for 2016 election candidates. The analysis includes a data frame comparison and a bar chart visualization.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

## Modlule 4 - Hospital Blood Pressure Analysis
This module analyzes a fictional hospital dataset containing patient blood pressure measurements, doctor assessments, and final decisions regarding immediate care. Boxplots and histograms were used to explore the distribution of blood pressure values and compare low versus high priority patients.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
Freq <- c(0.6, 0.3, 0.4, 0.4, 0.2, 0.6, 0.3, 0.4, 0.9, 0.2)

bloodp <- c(103, 87, 32, 42, 59, 109, 78, 205, 135, 176)

first <- c(1, 1, 1, 1, 0, 0, 0, 0, NA, 1)

second <- c(0, 0, 1, 1, 0, 0, 1, 1, 1, 1)

finaldecision <- c(0, 1, 0, 1, 0, 1, 0, 1, 1, 1)

hospital <- data.frame(Freq, bloodp, first, second, finaldecision)

boxplot(
  bloodp ~ finaldecision,
  data = hospital,
  names = c("Low Priority", "High Priority"),
  main = "Blood Pressure by Final Decision",
  ylab = "Blood Pressure"
)

hist(
  bloodp,
  main = "Histogram of Patient Blood Pressure",
  xlab = "Blood Pressure"
)
