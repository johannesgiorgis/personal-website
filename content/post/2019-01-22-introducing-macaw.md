---
title: "Introducing Macaw"
date: 2019-01-22T21:51:58-08:00
draft: false
metaAlignment: center
categories: ['projects']
tags: ['build']
keywords: ['tech']
---

Building a better Meetup.com Analytics and Search tool.

<!--more-->

<!-- toc -->

# Goal

Build a web based tool which allows you to do advanced searchs for Meetups. Specifically looking to add event frequency capabilities to quickly filter out non-active Meetups.

I will work on this project with my friend, [Andrew Key]. It is hosted on [Github]. 

## Project Stages

The project will have several stages. As of the start of the project, the below are the current stages:

- [ ] Data Collection either via Meetup API or Web Scraping
- [ ] Data Storage
- [ ] Exploratory Data Analysis
- [ ] Web based tool

## Change Log

- **2019-01-22**: Project Start; Create Github Repo; Write Introductory Blog Post 
- **2019-02-16**: Pivot to [Data Science Challenges]!

# Motivation

Last year, I moved to Vancouver, Canada. Before my move, I went to Meetup.com to find groups I could join and meet people. There were many interesting groups - hiking, photography, tech, career, etc. I signed up to so many groups and was looking forward to participating in them. What I soon discovered was that many groups were essentially dead - either they had their last event several months or even worse, a year ago or they never hosted an event, at least not on Meetup.com.

As you can imagine, the excitement of joining an awesome sounding group was immediately killed by the realization that this group never met. It might as well not even exist!

Furthermore, the Meetup.com search capabilities are quite lacking:

- You can search _Groups_ or _Calendar_
- You can browse upcoming or past meetups by date filtering by the ones you are going to, your Meetups only or also including suggestions
- You can search by group name, event name, matching keywords, etc
- You can search _Groups_ and sort them using different criteria (Recommended, Most active, Newest, Most members, Closest)

Although yes it has some search capabilities, there is no way to filter out non active groups or search for groups that meet weekly/monthly/bi-monthly, etc. As an example, I'd love to be able to quickly find the tennis Meetups that met at least once a month in the past 6 months.

<br/>

<!-- image classes="fancybox center clear" src="/images/post/2019-01-22-introducing-macaw/meetup_search_calendar.png" title="Meetup.com Calendar Search" >}} -->

<br/>

<!-- image classes="fancybox center clear" src="/images/post/2019-01-22-introducing-macaw/meetup_search_group.png" title="Meetup.com Group Search" >}} -->


[//]: # (References)

[Github]: https://github.com/johannesgiorgis/macaw
[Andrew Key]: https://github.com/redpanda-ai

[Data Science Challenges]: {{< ref "2019-02-16-introducing-datascience-challenges.md" >}}