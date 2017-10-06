# Load an prepare the data
## 1. Download the data and ensure that the working directory contains downloaded file (setwd())
[link to the data](https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip)
### Unzip/load the data
```r
if(!file.exists('activity.csv')){
    unzip('repdata%2Fdata%2Factivity.zip')
}
activityData <- read.csv('activity.csv')
```
## 2. Ensure that the date format is appropriate 
```r
activityData$Date <- as.Date(activityData$date, "%Y-%m-%d")
```
### Ensure that interval is a factor variable
```r
activityData$interval <- as.factor(activityData$interval)
```
### Exrtract levels of 5-min intervals
```r
l <- levels(activityData$interval)
```

