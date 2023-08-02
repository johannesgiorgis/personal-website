---
title: "Restarting My Blog"
date: 2023-08-01T20:37:13-07:00
draft: true
metaAlignment: center
categories: []
tags: []
#keywords: ['tech']
#thumbnailImage: //example.com/image.jpg
---

<!--more-->

Restarting my blog :)

First things first, let's update our theme from [hugo-tranquilpeak] to [hugo-PaperMod].

Why? The current theme I was using hasn't been updated since Aug 21, 2022 and I figured it would be a good way to freshen things about around here.

```sh
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive # needed when you reclone your repo (submodules may not get cloned automatically)
```

Next, I made a backup of my `config.toml` file and started editing away.

```sh
λ  lt *toml
.rw-rw-r--  434 johannes  1 Aug 20:01 netlify.toml
.rw-rw-r-- 8.9k johannes  1 Aug 21:42 old-config.toml
.rw-rw-r-- 8.9k johannes  1 Aug 21:50 config.toml
```

First item to change is of course the theme and run `hugo server -Dwv`:

- D to show drafts
- w to watch file for file changes
- v for verbose output

And we get our first failure, Something about a missing shortcode template.

```sh
λ  hugo server -Dwv
Start building sites … 
hugo v0.112.4-e285153d7f75d13bb062101c0a66b0138a90a71c+extended linux/amd64 BuildDate=2023-05-28T13:04:00Z VendorInfo=gohugoio
INFO 2023/08/01 20:38:20 syncing static files to /
INFO 2023/08/01 20:38:20 process in 0 ms
INFO 2023/08/01 20:38:20 assemble in 2 ms
Built in 34 ms
Error: error building site: assemble: "/home/johannes/src/personal-website/content/post/2019-01-06-how-i-build-this-site.md:323:1": failed to extract shortcode: template for shortcode "codeblock" not found
```

In an earlier attempt, I was commenting these lines out until I got the server running. This time, I smartened up (or took a wrong path) and decided to copy the missing shortcode templates from the old template's `layouts` directory to my own. TODO: link to commit portion if this approach remains.

After many server start failures and file copies, I got it working:

![layouts image](/images/post/2023-08-01-restarting-my-blog/2023-08-01-new-layouts.png)

And the result - pretty crappy! Let's beautify this

![initial website](/images/post/2023-08-01-restarting-my-blog/2023-08-01-initial-website-new-theme-papermod.png)

[hugo-tranquilpeak]: https://github.com/kakawait/hugo-tranquilpeak-theme
[hugo-PaperMod]: https://github.com/adityatelange/hugo-PaperMod
