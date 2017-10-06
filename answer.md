# Load an prepare the data
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
hist(totalSteps, breaks = 10, col = "red", main = "Total Number of steps each day", 
    xlab = "Average Total Number of Steps")
```
