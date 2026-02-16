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
```
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
```

## Module 5 - Matrix Analysis
This module explores matrix operations in R, specifically calculating determinants and inverses.

Two matrices were created using sequential values:

A <- matrix(1:100, nrow = 10)  
B <- matrix(1:1000, nrow = 10)

Matrix A is a 10 × 10 square matrix, while matrix B is a 10 × 100 rectangular matrix. Only square matrices can have determinants and inverses.

The determinant of matrix A was calculated using the det() function and the result was 0. A determinant of zero indicates that the matrix is singular, meaning it does not have an inverse. When attempting to compute the inverse using solve(A), R returned an error confirming that matrix A cannot be inverted.

Matrix B is not square, so R returned errors when attempting to compute both its determinant and inverse. This demonstrates that determinants and inverses are only defined for square matrices.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
A <- matrix(1:100, nrow = 10)
B <- matrix(1:1000, nrow = 10)

dim(A)
dim(B)

detA <- det(A)
detA

invA <- tryCatch(solve(A), error = function(e) e$message)
invA

detB <- tryCatch(det(B), error = function(e) e$message)
detB

invB <- tryCatch(solve(B), error = function(e) e$message)
invB
```
