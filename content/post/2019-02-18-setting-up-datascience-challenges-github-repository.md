---
title: "Setting Up Data Science Challenges Github Repository"
date: 2019-02-18T19:06:40-08:00
draft: false
metaAlignment: center
categories: ['projects']
tags: ['data science challenges', 'git']
keywords: ['tech', 'data science']
---

Forking my own repository.

<!--more-->

# Background 

Over the past weekend, [Andy] and I setup the [Data Science Challenges] repository on [Github]. The intention is to have this repository host the challenges organized in their own respective folders and using Markdown for the content. We would update the repository as we came up with more challenges. Anyone could follow along by forking the repo and working on their forked repo. They could get the latest updates by pulling the master repo.

With the master repository being my own, I couldn't follow the conventional method of forking the repository. I had to find another way. This post details how I went about it.

# Solution

Following along this [Fork Your Own Github Repository Article], I created a new repository with a remote reference to the original master repository. 

1. Create a new repository on Github (`ds_challenges`)

2. Clone the new repository

	`git clone git@github.com:johannesgiorgis/ds_challenges.git`

3. Add a reference to the original repository

	```
	cd ds_challenges/

	git remote add upstream git@github.com:johannesgiorgis/datascience_challenges.git
	```

4. Pull content from the original repository to the new repository

	`git pull upstream master`

5. Push content to the new repository

	`git push origin master`

And voila! Now my repository (`ds_challenges`) was tracking the master repository (`data_science_challenges`).

In the future as we add more challenges to the master repository, I can update my new repository by:

`git pull upstream master`

Such a brilliant solution and I really give kudos to the author of the article that I followed, Mike Zrimesk. Hopefully my article can in turn help someone else who faces a similar issue.

[//]: # (References)

[Github]: https://github.com/johannesgiorgis/datascience_challenges
[Andy]: https://github.com/redpanda-ai
[Fork Your own Github Repository Article]: https://medium.com/@mikezrimsek/fork-your-own-github-repository-19ad4582b50a

[Data Science Challenges]: {{< ref "2019-02-16-introducing-datascience-challenges.md" >}}