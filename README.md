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

## Module 11 - Tufte Visualizastion in R

This module recreates a visualization from Dr. Piwek’s Tufte post using R. It focuses on customizing a simple plot with labels and formatting to improve clarity and presentation.

Blog link: https://wesleyhuang7.wixsite.com/r-programming-journa

### R Code

```r
x <- 1967:1977
y <- c(0.5, 1.8, 4.6, 5.3, 5.3, 5.7, 5.4, 5.0, 5.5, 6.0, 5.0)

plot(
  y ~ x,
  axes = FALSE,
  xlab = "",
  ylab = "",
  pch = 16,
  type = "b"
)

axis(1, at = x, labels = x, tick = FALSE, family = "serif")

axis(
  2,
  at = seq(1, 6, 1),
  labels = sprintf("$%s", seq(300, 400, 20)),
  tick = FALSE,
  las = 2,
  family = "serif"
)

abline(h = 6, lty = 2)
abline(h = 5, lty = 2)

text(
  max(x),
  min(y) * 2.5,
  "Per capita\nbudget expenditures\nin constant dollars",
  adj = 1,
  family = "serif"
)

text(
  max(x),
  max(y) / 1.08,
  labels = "5%",
  family = "serif"
)
```
