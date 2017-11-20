---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data
List of the steps that are performed are :  
1. Read the data  
2. Sum the number of steps taken in a day while removing NA  
3. Plot the histogram of the total number of steps every day  

```r
rawData <- read.csv("./activity/activity.csv")
totalSteps <- tapply(X = rawData$steps, INDEX = rawData$date, FUN = sum, na.rm  = TRUE)
hist(totalSteps)
```

![](PA1_template_files/figure-html/preprocess-1.png)<!-- -->

## What is mean total number of steps taken per day?


```r
meanSteps <- tapply(X = rawData$steps, INDEX = rawData$date, FUN = mean, na.rm  = TRUE)
hist(meanSteps)
```

![](PA1_template_files/figure-html/meanAndMedian-1.png)<!-- -->

```r
medianSteps <- tapply(X = rawData$steps, INDEX = rawData$date, FUN = median, na.rm  = TRUE)
hist(medianSteps)
```

![](PA1_template_files/figure-html/meanAndMedian-2.png)<!-- -->

## What is the average daily activity pattern?


```r
avgSteps <- tapply(X = rawData$steps, INDEX = rawData$interval, FUN = mean, na.rm  = TRUE)
plot(avgSteps, type = "l")
points(which.max(avgSteps),max(avgSteps), col ="red", pch = 16)
```

![](PA1_template_files/figure-html/averageDailyPattern-1.png)<!-- -->
The interval that takes the maximum steps is 104.

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
