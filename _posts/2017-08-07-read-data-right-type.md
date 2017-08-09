---
layout: post
title: "How to read data with correct types in R?"
description: "reading data in R"
category: r
tags: [R, statistics]
comments: true
---

Wrong data type can be a serious headache sometimes. It is something easy to overlook until some bugs jump into your sight. Here I will summarise several ways to avoid this type of mistakes.
1. numeric type changes to character. 
Sometimes, there are weird data mingled in your numeric data, such as "-", or "1 not". Sometimes, it can be obvious, sometimes not. `as.numeric` solves most of them. It may cause warnings, so you may want to wrap with `suppresswarnings(as.numeric())`.
You can avoid it beforehand when reading data in. In `read.csv`, you can use `colClasses` argument to specify. It actually can reduce your loading time. The possible values are "NA"(default), "NULL"(skipped), "logical", "integer", "numeric", "complex", "character", "raw", "factor", "Date", or "POSIXct". For missing value, `na.strings` argument can be specified. It can be a vector of strings. Blank fields are automatically considered to be missing no matter it is specified or not.
In `read_excel`, `col_types` can be specified. "NULL" means guessing all columns. A vector is used to speficy each column. The possible values can be "skip", "guess", "logical", "numeric", "data", "text" or "list". For missing values, `na` argument can be specified. By default, it is "". 
2. character changes to factor type.
This sometimes can cause serious headache. Pre-specify the type when readding data is a good habit. 
In `read.csv`, the characters are converted to factor by default. If conversion is not desired, set `stringAsFactors` as FALSE, or set `colClasses` specifically.  
