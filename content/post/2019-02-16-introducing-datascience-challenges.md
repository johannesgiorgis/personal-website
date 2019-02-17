---
title: "Introducing Data Science Challenges"
date: 2019-02-16T18:15:27-08:00
draft: false
metaAlignment: center
categories: ['projects']
tags: ['data science challenges']
keywords: ['tech', 'data science']
---

Become a better Data Scientist by working on Data Science Challenges. Because that's what heroes do!

<!--more-->

# Introduction

Data Science Challenges is an opportunity to flex your data science muscles by working on various types of Data Science projects. Projects will span the full gamut of Data Science - from working with APIs to cleaning, analyzing and visualizing data, to building machine learning models and deploying them as web applications/services.

My hope for this project is that it enables anyone interested in Data Science to expand upon their existing skills by building hands on open ended projects. This project is aimed at people who are comfortable programming, have gone through some MOOCs and are looking to challenge themselves by applying their knowledge and skills.

Interested in getting started? Here is the [Github] repo that you fork.

# Background

A few weeks ago, [Andrew Key] and I started working on a project called [macaw]. The goal was to build better search and filtering capability for Meetups. Building the project would have encompassed web scraping, working with Meetup's API, building a data pipeline and API, etc. So it was also an opportunity for us to flex our data science muscles. Following the project's launch, we discussed lots of cool engineering ideas and viable paths.

A few weeks later, we had nothing but an initial demo script showcasing the capabilities of [Meetup's API] that Andy had written. We weren't making much progress.

More importantly than the Meetup functionality I was so wishing we could build, we weren't flexing our data science muscles. Mostly because I was stuck in analysis paralysis trying to start this project by scraping Meetup.com and being overwhelmed by the sheer number of paths we could take.

So we decided to switch things up by challenging ourselves.


# Pivot to Challenging Ourselves!

We challenged each other to use the Meetup API to come up with a list of Meetups that were based in our respective cities (San Francisco, California and Vancouver, British Columbia) within 1 hour.

And Data Science Challenges was born!

Well... not quite yet.

We got to working and ended up spending about 90 minutes before re-convening to see how much progress we had each made. We didn't even end up answering our original question.

At a high level, we both ended up with very interesting insights which would require further time to dive deeper into. (As a teaser, did you know there is a Tech Meetup group in Vancouver with over 36,000 members when most (almost ~90%) are made up of ~1700 members? Crazy!) Again, we saw so many possibilities of taking the next steps. But this time, we were more disciplined! We decied to give ourselves 1 week to further explore the data, come up with insights and to blog about them.

So what happened next? What brilliant insights did we learn about our local Meetups?

...Not much. Well, we hit a logistical issue - we were working off of one branch in our repo which we had both made changes to locally. Yes, yes we could have easily solved it. That's not the point. We wanted to make it more clean, organized and easily accessible to folks. So we got to thinking...


# A New Idea is Born

We both really enjoyed the structure we had created: 

1. Come up with an open-ended question, give yourself a set amount of time to see what you could explore and find
2. Then give yourself some more time to dig deeper into this rabbit hole and 
3. Write up about your findings to share with the world.

But we needed some more structure:

- We needed a place to host the challenges and make them easily accessible to anyone who wanted to use them
- We needed a place to work on the challenges independently
- We needed a place to write up about our findings

So what did we do?

We created a [Github] repository to host the challenges themselves as Markdown files, organizing each challenge into its own folder. We both forked this repository to create our own, so we could work on them independently without clashing with each other.

And Data Science Challenges was born! Yes for real this time :)


# Why Data Science Challenges

For me, Data Science Challenges was created due to a few reasons:

First, you learn by lots of trial and error. I can't find the original story, but it goes something like this: A teacher split a group of students into two camps. One camp had to come up with the most perfect work of art, while the second camp was free to create and iterate many works. At the end of the period, the teacher looked at what the students had created. The 'perfect' camp had struggled to create one perfect work of art and most were stuck in analysis paralysis. The 'iterative' camp had ended up creating lots of great work as they were able to iterate and evolve their ideas without the fear of trying to create 1 perfect work of art.

Most likely, I have messed up the details and a quick Google search didn't yield much results in finding the original story. But the main point which stuck with me was: you get better by trying and iterating on your original ideas, not by trying to create 1 perfect work of art. This also was very true for me at work. Initial programs I had written were terrible and often times broke in production, but by iterating and improving them, I made them become very stable and reliable. Nothing is built over night. Its through lots of trial and error.

Secondly, I was in a stage in my Data Science learning where another Introductory tutorial or MOOC wasn't very valuable to me. Sure, repeating concepts over and over again as I mentioned above is a valuable learning tool, but you should also stretch your muscle and learn something that challenges you. I needed an applied hands on project that wasn't introductory in nature yet not so vast and open ended it left me clueness as what I should do next. Of course, you can decide to go super deep in any of these areas and build some awesome stuff.

Thirdly, I wanted exposure to various Data Science skills - cleaning data, visualizing data, building Machine Learning models - within a scoped area. I had been reading a lot about building a Data Science Portfolio, how you should focus on 1-2 big projects, etc.




[//]: # (References)

[Github]: https://github.com/johannesgiorgis/datascience_challenges
[Andrew Key]: https://github.com/redpanda-ai
[Meetup's API]: https://www.meetup.com/meetup_api/
[PyBites' Code Challenges]: https://pybit.es/pages/challenges.html

[macaw]: {{< ref "2019-01-22-introducing-macaw.md" >}}
