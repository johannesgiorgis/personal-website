---
title: "Discovering Command Line Tools"
date: 2019-03-05T22:11:17-08:00
draft: true
metaAlignment: center
categories: ['cli-tools']
tags: ['tools', 'cli']
---

Discovering and keeping track of useful Command Line Tools.

<!--more-->

<!-- toc -->

# Introduction

I spend a large part of my day working in the terminal - either I'm using `vim` to code (sometimes you just got to use the available tools) or navigating a server to troubleshoot a production issue. So I always appreciate discovering new tools that make my time in the terminal more productive and enjoyable.

This page is dedicated to discovering and keeping track of the various useful Command Line tools I come across.


## q

`Check out "q" - It let's you query csv from terminal.` 

That's the message my friend, Rizwan sent me introducing me to a pretty cool tool, [q].

**So what is it?**

[q] is a command line tool that allows you to run SQL-like queries on any tabular text file (CSVs, TSVs, etc). The project's home page shows the below 2 examples:

```
q "SELECT COUNT(*) FROM ./clicks_file.csv WHERE c3 > 32.3"
```


```
ps -ef | q -H "SELECT UID,COUNT(*) cnt FROM - GROUP BY UID ORDER BY cnt DESC LIMIT 3"
```

No need to set up and insert data in a database. Just have your files or processes ready and you can start querying them. How awesome is that?

It reminds me of [AWS Athena], which allows you to start querying your data on [AWS S3] instantly without needing to go through the hassle of an ETL process or having to move your data into a database. You get the benefits of dealing only with files on AWS S3, while still reaping the benefits of SQL queries, all without setting up one server or moving your data. Talk about a triple win!

We had previously used Athena for some ad-hoc analysis or our S3 data usage at work, but recently we started using it as part of a tool in production on a regular basis, the benefits are much more pronounced.

So back to q - this looks like a very convenient tool to add to my tool belt. I look forward to using it in the near future.

[//]: # (Reference Links)

[q]: http://harelba.github.io/q/
[AWS Athena]: https://aws.amazon.com/athena/
[AWS S3]: https://aws.amazon.com/s3/