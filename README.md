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
