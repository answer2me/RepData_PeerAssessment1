#Load an prepare the data
##Download the data and ensure that the working directory contains downloaded file (setwd())

##Unzip/load the data
if(!file.exists('activity.csv')){
    unzip('repdata%2Fdata%2Factivity.zip')
}
activityData <- read.csv('activity.csv')

##Ensure that the date format is appropriate 
activityData$Date <- as.Date(activityData$date, "%Y-%m-%d")

##Ensure that interval is a factor variable
activityData$interval <- as.factor(activityData$interval)

## Exrtract levels of 5-min intervals
l <- levels(activity$interval)
