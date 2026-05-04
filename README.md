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

## Module 6 – Matrix Operations in R

This module explores matrix operations in R, including matrix addition, subtraction, diagonal matrices, and constructing matrices using the diag() function.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
# Create matrices A and B
A <- matrix(c(2, 0, 1, 3), ncol = 2)
B <- matrix(c(5, 2, 4, -1), ncol = 2)

# Display matrices
A
B

# Matrix addition
A + B

# Matrix subtraction
A - B

# Create diagonal matrix of size 4
diag_matrix <- diag(c(4, 1, 2, 3))
diag_matrix

# Generate the required 5x5 matrix
M <- diag(3, 5)
M[,1] <- c(3, 2, 2, 2, 2)
M
```
## Module 7 – Object-Oriented Systems in R (S3 vs S4)

This module explores object-oriented programming concepts in R using a custom dataset. The assignment demonstrates generic functions, object types, and differences between S3 and S4 systems.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
# Create custom dataset
students <- data.frame(
  name = c("Alex", "Brian", "Cathy", "Diana", "Evan"),
  age = c(20, 21, 19, 22, 20),
  GPA = c(3.4, 3.7, 3.2, 3.9, 3.5)
)

students

# Generic functions and object inspection
class(students)
typeof(students)
isS4(students)

summary(students)
head(students)

# S3 example
s3_student <- list(name = "Myself", age = 29, GPA = 3.5)
class(s3_student) <- "student"

print.student <- function(x) {
  cat("Student Name:", x$name, "\n")
  cat("Age:", x$age, "\n")
  cat("GPA:", x$GPA, "\n")
}

s3_student

# S4 example
setClass(
  "student",
  slots = list(
    name = "character",
    age = "numeric",
    GPA = "numeric"
  )
)

s4_student <- new(
  "student",
  name = "Myself",
  age = 29,
  GPA = 3.5
)

s4_student
```
## Module 8 – Importing, Grouping, and Filtering Data in R

This module imports a dataset, calculates mean grade by sex using the `plyr` package, filters student names containing the letter i, and exports the results to CSV files.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
library(plyr)

students <- read.table(file.choose(), header = TRUE, sep = ",")

students

students_gendered_mean <- ddply(students, "Sex", transform, Grade.Average = mean(Grade))

students_gendered_mean

write.table(students_gendered_mean, "Students_Gendered_Mean.csv", sep = ",", row.names = FALSE)

i_students <- subset(students, grepl("[iI]", students$Name))

i_students

write.table(i_students, "I_Students.csv", sep = ",", row.names = FALSE)
```
## Module 9 – Visualization Systems in R

This module compares three visualization systems in R: base graphics, lattice, and ggplot2 using the iris dataset. It demonstrates how each system creates visualizations and highlights differences in syntax, flexibility, and output quality.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
data("iris")
head(iris)

library(lattice)
library(ggplot2)

# Base R Plot
plot(
  iris$Sepal.Length,
  iris$Petal.Length,
  main = "Base R: Sepal Length vs Petal Length",
  xlab = "Sepal Length",
  ylab = "Petal Length",
  col = as.numeric(iris$Species),
  pch = 19
)

# Lattice Plot
xyplot(
  Petal.Length ~ Sepal.Length | Species,
  data = iris,
  main = "Lattice: Petal Length vs Sepal Length by Species",
  xlab = "Sepal Length",
  ylab = "Petal Length"
)

# ggplot2 Plot
ggplot(iris, aes(x = Sepal.Length, y = Petal.Length, color = Species)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE) +
  labs(
    title = "ggplot2: Sepal Length vs Petal Length by Species",
    x = "Sepal Length",
    y = "Petal Length"
  )
```

## Module 11 - Debugging Tukey Outlier Function

This module focuses on reproducing, diagnosing, and fixing a bug in an R function that detects rows of a numeric matrix that are outliers in every column using the Tukey rule. The corrected version replaces an incorrect logical operator and adds simple defensive checks for safer use.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
tukey.outlier <- function(x, k = 1.5) {
  q1 <- quantile(x, 0.25, na.rm = TRUE)
  q3 <- quantile(x, 0.75, na.rm = TRUE)
  iqr <- q3 - q1
  x < (q1 - k * iqr) | x > (q3 + k * iqr)
}

tukey_multiple <- function(x) {
  outliers <- array(TRUE, dim = dim(x))
  for (j in 1:ncol(x)) {
    outliers[, j] <- outliers[, j] && tukey.outlier(x[, j])
  }
  outlier.vec <- vector("logical", length = nrow(x))
  for (i in 1:nrow(x)) {
    outlier.vec[i] <- all(outliers[i, ])
  }
  return(outlier.vec)
}

set.seed(123)
test_mat <- matrix(rnorm(50), nrow = 10)

# Uncomment this line only when you want to reproduce the error
# tukey_multiple(test_mat)

corrected_tukey <- function(x) {
  if (!is.matrix(x)) {
    stop("x must be a matrix.")
  }
  if (!is.numeric(x)) {
    stop("x must be a numeric matrix.")
  }

  outliers <- array(TRUE, dim = dim(x))
  for (j in seq_len(ncol(x))) {
    outliers[, j] <- outliers[, j] & tukey.outlier(x[, j])
  }

  outlier.vec <- logical(nrow(x))
  for (i in seq_len(nrow(x))) {
    outlier.vec[i] <- all(outliers[i, ])
  }

  outlier.vec
}

corrected_tukey(test_mat)
```

## Module 12 – R Markdown Primer

This module introduces the basics of R Markdown by combining narrative writing, LaTeX math, and executable R code in one document. The final output was knitted to HTML to show how source code and rendered results work together in a reproducible workflow.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
---
title: "My R Markdown Primer"
author: "Wesley Huang"
date: "April 13, 2026"
output: html_document
---

# Introduction

R Markdown is a file format that lets you combine regular writing, R code, and formatted output in one document. It is useful because it keeps the explanation and the analysis together, which makes the work easier to follow and reproduce.

This is a simple example of narrative text written in Markdown. One helpful part of R Markdown is that it can mix normal paragraphs with code chunks and math expressions in the same file.

An inline math example is $\alpha + \beta = \gamma$.

A displayed equation example is:

$$
y = mx + b
$$

# Load Data

```{r}
library(ggplot2)
data(mtcars)
head(mtcars)
```

# Summary Statistics

The code chunk below gives a quick summary of the dataset.

```{r}
summary(mtcars)
```

# Visualization

The next code chunk creates a scatter plot showing the relationship between car weight and miles per gallon.

```{r}
ggplot(mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(
    title = "Miles Per Gallon vs Car Weight",
    x = "Weight",
    y = "Miles Per Gallon"
  )
```

# Reflection

Using R Markdown was different from writing a plain report because it allowed me to keep my writing, code, and results together in one place. I liked that the output updated directly from the code, which makes the document more organized and reproducible. One thing I noticed is that formatting matters a lot, so even small mistakes in chunk syntax or Markdown symbols can affect the final output.
```

```
## Final Project – R Markdown Primer

This project focuses on learning the basics of R Markdown by combining writing, LaTeX math, and executable R code into one document. The final report was knitted to HTML to demonstrate how code and output can be presented together in a clean and organized way.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### Files
- module12_markdown_primer.Rmd
- module12_markdown_primer.html
```
