---
title: "Best Vancouver Technology Meetups of 2019"
date: 2019-03-04T21:46:42-08:00
draft: true
metaAlignment: center
categories: ['projects']
tags: ['data science challenges']
keywords: ['tech', 'data science', 'vancouver', 'meetup']
---

First Data Science Challenge Write Up - Discovering Top Technology Meetups in Vancouver.

<!--more-->

# Challenge

My friend [Andy Key] and I introduced a new feature series, [Data Science Challenges] \(DSC).

The purpose of DSC is to: 

1. Challenge us to use and expand our Software Engineering and Data Science skills
2. Apply these skills to solve problems and discover new insights
3. Build a portfolio of projects that range the full gamut of the Data Science Lifecycle

Our [first challenge] was to use the [Meetup API] to explore meetups in our city of choice.

For my challenge, I chose to explore Technology Meetup Groups in my city, beautiful **Vancouver, BC**.


# Exploring Vancouver Tech Meetups

I wanted to explore the group’s various traits (number of members, location, compare smallest vs largest groups, group ratings, etc) and look at how often the largest groups hosted events and their attendance numbers. My intention was to discover and learn more about the groups and potentially come up with a list of recommended groups to join.

Check out my [notebook] for the full details.

This blog post covers:

- Recommendations
- Discoveries
- How I tackled this challenge
- Conclusion
- How you can join Data Science Challenges

Without further delay, let’s see our recommendations.

# Recommendations

So what are my recommendations for which of the largest and most active Tech Meetup groups you should join?

**4th Place**

If you are into Web Development and Design and don’t mind joining a group that meets once every few months, but that attracts a large number of attendees, you should join the following groups:

- [The Vancouver Web Design Meetup Group]
- [VanJS: Vancouver JavaScript Developers]

**3rd Place**

If you want to join a Tech Meetup Group that meets at least once a month and has a lot of attendees, you should join the following groups:

- [Agile Vancouver]
- [Full Indie]
- [HackerNest Vancouver Tech Socials]
- [NetSquared Vancouver: Tech4Good and Nonprofits]
- [TechVancouver]

**2nd Place**

If you want to join an Entrepreneurship and Startups focused Meetup Group that meets several times a month and has a decent but sometimes inconsistent attendance, you should join the following group:

- [YVR Startups]

**1st Place**

If you are into Data Science and want to join a Meetup Group that meets several times a week and has lots of attendees, you should join the following group:

- [Learn Data Science]

{{< wide-image src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/learn_data_science_meetup.png" title="Learn Data Science Meetup" >}}


# Discoveries

**Note**: For the purposes of this analysis, the largest and smallest groups were defined below:

- **Largest groups** were defined as groups with **more than 10x the size of the median number of members**
- **Smallest groups** were defined as groups with **less than 1/10th of the median number of members**

With the median being _295_, the largest groups had more than _3000_ members while the smallest groups had less than _30_ members.

### Size of Groups

- Average number of members is **680**
- Almost **80%** of groups have less than **900** members

{{< image classes="center" src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/members_histogram.png" title="Members Histogram" >}}

<br/>

{{< image classes="center" src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/members_frequency_table.png" title="Members Frequency Table" >}}

### Largest vs. Smallest Groups

- The largest groups tended to be **centered around Downtown and the surrounding areas** while the smallest groups were more spread across the city.

{{< wide-image src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/largest_vs_smallest_meetups_locations.png" title="Location of Smallest and Largest Tech Groups" >}}

<br/>

- Largest groups were not rated higher than smaller groups
- Most groups were rated very high (**>4.0**)

{{< image classes="center" src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/meetup_ratings.png" title="Member vs Ratings for Largest vs Non-Largest Groups" >}}

<br/>

- The smallest groups had a rating of **0**

{{< image classes="center" src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/smallest_groups_unique_columns.png" title="All 30 Smallest Groups had 1 Rating: 0" >}}




### Largest Group Events

The following Meetups meet frequently (once to multiple times a month) and are either maintaining or increasing their attendance:

- _Agile Vancouver_
- _Full Indie_
- _HackerNest Vancouver Tech Socials_
- _NetSquared Vancouver: Tech4Good and Nonprofits_
- _TechVancouver_
- _Learn Data Science_

{{< wide-image src="/images/post/2019-03-04-best-vancouver-technology-meetups-of-2019/rsvps_vs_time_plot.png" title="Yes RSVP’s over Time Plot — Data and Regression Model Fits" >}}


# How did I go about it?

Going into this challenge, I had never used the Meetup API before, so the first step was to understand the [Meetup API Module] and the available methods. In order to get Tech Meetup groups in Vancouver, I had to provide the Category ID, City and Country Code. Figuring out the correct values for these and understanding how the Meetup API v2’s response payloads returned pages was the preliminary activity.

After some trial and error and a couple of helper functions later, I had all the Tech Groups based in Vancouver, BC and a few of the surrounding cities. Next, I did some initial data exploration. Looking at parts of the data, the uniqueness, data ranges, and tendencies of each column allowed me to make more discoveries, raise more questions and clean up my data.

Once the initial clean up was done, I was able to:

- Look at the size of the groups via plots and frequency tables
- Compare largest and smallest groups
- Compare ratings of the largest groups against the other groups
- Look at groups with no ratings

One of the indicators of a good Meetup group to join is the frequency and attendance of the events they host. Focusing exclusively on the 17 largest groups, I looked at the events they hosted over the past 6 months. After cleaning up the events data, I merged it with the groups' data and started analyzing the data. This analysis led to my recommended list of Meetups to join.

# Conclusions

This was a very exciting and rewarding project with some interesting findings. It was great to utilize both my data (exploration, visualization, cleaning) and software engineering skills to learn more about the Meetups in my city.

There are definitely additional areas to explore, and I hadn’t answered all the questions I had raised. The fact that I focused exclusively on the largest Meetups also makes this recommendation list a bit biased. Surely there are smaller Meetups which meet frequently enough to recommend people. I will treat that and the additional questions as project extension ideas for the future.

For now, it’s on to the next Data Science Challenge!

# So how do I do the Data Science Challenges thingy?

Oh, you’re still reading? Well, if you are comfortable with Programming, Statistics, Data Science and are looking to take your skills to the next level by applying your them to solve open-ended problems that interest you, I have written an [excellent introduction] that will help you get started.


[//]: # (References)

[first challenge]: https://github.com/johannesgiorgis/datascience_challenges/tree/master/01_explore_meetup_api
[Meetup API]: https://www.meetup.com/meetup_api/
[notebook]: https://nbviewer.jupyter.org/github/johannesgiorgis/ds_challenges/blob/master/01_explore_meetup_api/explore_vancouver_meetups.ipynb?flush=true

[The Vancouver Web Design Meetup Group]: https://www.meetup.com/webdesign-395/
[VanJS: Vancouver JavaScript Developers]: https://www.meetup.com/vancouver-javascript-developers/
[Agile Vancouver]: https://www.meetup.com/vancouver-javascript-developers/
[Full Indie]: https://www.meetup.com/Vancouver-Indie-Game-Developers/
[HackerNest Vancouver Tech Socials]: https://www.meetup.com/HackerNestVAN/
[NetSquared Vancouver: Tech4Good and Nonprofits]: https://www.meetup.com/net2van/
[TechVancouver]: https://www.meetup.com/TechVancouverOrg/
[YVR Startups]: https://www.meetup.com/YVR-Startups/
[Learn Data Science]: https://www.meetup.com/LearnDataScience/

[Meetup API Module]: https://meetup-api.readthedocs.io/en/latest/meetup_api.html

[Github]: https://github.com/johannesgiorgis/datascience_challenges
[DS Challenges]: https://github.com/johannesgiorgis/ds_challenges
[master repository]: https://github.com/johannesgiorgis/datascience_challenges
[Andy Key]: https://medium.com/@andrew.key

[Data Science Challenges]: {{< ref "2019-02-16-introducing-datascience-challenges.md" >}}
[excellent introduction]: {{< ref "2019-02-16-introducing-datascience-challenges.md" >}}