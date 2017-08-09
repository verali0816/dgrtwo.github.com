---
layout: post
title: "How to read data in R?"
description: "reading data in R"
category: r
tags: [R, statistics]
comments: true
---
How to read data in R?

Programming language is like any other kind of language. You use it oftenly, then you are good at it. You do not use it recently, you forget it. I have been in a pain when I am facing a new type of data to read for different purpose. So I am going to collect as more as scinarios here and share them with other people. Well, of course, now basically no one knows this website. This will not be a comprehensive review of all the arguments in every function. Instead, it will be a ready-to-use code for different situations.

Let's begin!

1. Use base R to read everything from a csv file. Say we have this training.csv file. Well, it does not have header.

```r
read.csv("training.csv", header = FALSE) #the default header is TRUE for read.csv
```
Play with row.names and col.names. If a single number is given, then use that column or row to be rownames or colnames. If a vector is given, then they will be the new names. If using them together, like the case below, you still need to give a extra colname, but it will not show. 
```r
read.csv("training.csv", header = FALSE, row.names = 1, col.names = c("c1","c2","c3", "c4", "c5", "c6"))
```

2. For excel files, xls or xlsx, I am used to use readxl package.

```r
read_excel(path, sheet = NULL, range = NULL, col_names = TRUE,
  col_types = NULL, na = "", trim_ws = TRUE, skip = 0, n_max = Inf,
  guess_max = min(1000, n_max))
```

```r
library(readxl)
read_excel("trainingxls.xls", col_names = FALSE)
```
colnames will be "X1, X2...". 

Specify the range to read,
```r
xx = read_excel("trainingxls.xls", col_names = FALSE, range = cell_rows(1:4))
xx = read_excel("trainingxls.xls", col_names = FALSE, range = "C1:E7")
xx = read_excel("trainingxls.xls", col_names = FALSE, range = "R1C2:R2C5")
xx = read_excel("trainingxls.xls", col_names = FALSE, range = cell_cols("B:D"))
```
read_xls and read_xlsx are the same.
