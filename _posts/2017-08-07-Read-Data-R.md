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
