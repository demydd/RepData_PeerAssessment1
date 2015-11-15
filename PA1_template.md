---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
  keep_md: true
---

To set up necessary packages and libraries:

```r
  #to install packages if it is required
  if (!require("dplyr")){
    install.packages("dplyr")
  }
```

```
## Warning: package 'dplyr' was built under R version 3.2.2
```

```r
  if (!require("ggplot2")){
    install.packages("ggplot2")
  }
```

```
## Warning: package 'ggplot2' was built under R version 3.2.2
```

```r
  if (!require("lubridate")){
    install.packages("lubridate")
  }
```

```
## Warning in library(package, lib.loc = lib.loc, character.only = TRUE,
## logical.return = TRUE, : there is no package called 'lubridate'
```

```
## package 'lubridate' successfully unpacked and MD5 sums checked
## 
## The downloaded binary packages are in
## 	C:\Users\Demyd\AppData\Local\Temp\RtmpY5w9TG\downloaded_packages
```

```r
  if (!require("lattice")){
    install.packages("lattice")
  }

  #to install libraries if it is required
  if (!require(dplyr)){
    library(dplyr)  
  }

  if (!require(ggplot2)){
    library(ggplot2)  
  }  
  if (!require(lubridate)){
    library(lubridate)
  }
```

```
## Warning: package 'lubridate' was built under R version 3.2.2
```

```r
  if (!require(lattice)){
    library(lattice)
  }
```

###**Copy data source file into work directory!!!**#####

## Loading and preprocessing the data

The data loading is with: read.csv() function.
To change data into tbl format to analyze further:


```r
setwd("D:/Demyd/Personal/Coursera/Reproducible Research/Project")
```

```
## Error in setwd("D:/Demyd/Personal/Coursera/Reproducible Research/Project"): cannot change working directory
```

```r
data<-read.csv("activity.csv")
```

```
## Warning in file(file, "rt"): cannot open file 'activity.csv': No such file
## or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```r
tbl_data<-tbl_df(data)
```

```
## Error: data is not a data frame
```

```r
rm(data)
```

```
## Warning in rm(data): object 'data' not found
```

```r
head(tbl_data)
```

```
## Error in head(tbl_data): object 'tbl_data' not found
```


## What is mean total number of steps taken per day?

- to remove NA from the subset

```r
rm_na<-filter(tbl_data,!is.na(steps))
```

```
## Error in filter_(.data, .dots = lazyeval::lazy_dots(...)): object 'tbl_data' not found
```
- group data, summarize and make the histogram:

```r
by_date<-group_by(rm_na,date) 
```

```
## Error in group_by_(.data, .dots = lazyeval::lazy_dots(...), add = add): object 'rm_na' not found
```

```r
total<-summarize(by_date,total=sum(steps))
```

```
## Error in summarise_(.data, .dots = lazyeval::lazy_dots(...)): object 'by_date' not found
```

```r
with(total,hist(total,10,col=date
                ,main="Total step frequancy per one day"
                ,xlab="The total steps per one day"))
```

```
## Error in with(total, hist(total, 10, col = date, main = "Total step frequancy per one day", : object 'total' not found
```

- calculate mean and median:


```r
mean<-mean(total$total)
```

```
## Error in mean(total$total): object 'total' not found
```

```r
median<-median(total$total)
```

```
## Error in median(total$total): object 'total' not found
```





























