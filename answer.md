Load the data

## Url of the data zip file
fileUrl <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip"

# Downlaod zip file download.file(fileUrl, destfile='activity.zip', method='curl')

# Unzip the data file. Use read.csv() to load the data set into R
activity <- read.csv(unz("activity.zip", "activity.csv"))
activityCopy <- activity

# Convert date to date class
activity$Date <- as.Date(activity$date, "%Y-%m-%d")

# Convert interval to a factor
activity$interval <- as.factor(activity$interval)

# Exrtract levels of 5-min intervals
l <- levels(activity$interval)
