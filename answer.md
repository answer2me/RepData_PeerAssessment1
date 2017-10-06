# Load an prepare the data
```r
# Load libraries
library(ggplot2)
```

## Download the data and ensure that the working directory contains downloaded file (setwd())
[link to the data](https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip)

```r
# Unzip/load the data
if(!file.exists('activity.csv')){
    unzip('repdata%2Fdata%2Factivity.zip')
}
activityData <- read.csv('activity.csv')
```
## Ensure that the date format is appropriate 
```r
activityData$Date <- as.Date(activityData$date, "%Y-%m-%d")
```

```r
# Ensure that interval is a factor variable
activityData$interval <- as.factor(activityData$interval)
```

```r
# Exrtract levels of 5-min intervals
l <- levels(activityData$interval)
```
## Histograms of the total number of steps taken each day
```r
# Calculate total steps 
totalSteps <- tapply(activityData$steps, activityData$date, sum, na.rm = T)
```
```r
# Create a histogram 
hist(totalSteps, breaks = 50, col = "blue", main = "Total Number of steps each day", 
     xlab = "Total Number of Steps")
```
![plot of Rplot](Rplot.png) 

```r
# Mean and median number of steps taken each day
totalStepsMean <- mean(totalSteps)
totalStepsMedian <- median(totalSteps)
```

## Time series plot of the average number of steps taken
```r
# Calculate the average number of steps grouped by intereval
averageSteps = tapply(activityData$steps, activityData$interval, mean, na.rm = T)
```
```r
# Convert levels of intervals into numeric
Interval <- as.numeric(l)
```
```r
# Data frame is created in order to plot the data
df <- data.frame(averageSteps, Interval)
```
```r
#plot
ggplot(df, aes(Interval, averageSteps)) + geom_line(colour = "blue") + ggtitle("Time series plot") + 
    ylab("Average Number of Steps")
 ```
 ![plot of Rplot2](Rplot2.png) 
