---
title: "Updating Site Theme Version"
date: 2023-08-28T23:43:01-07:00
draft: true
metaAlignment: center
categories: []
tags: []
#keywords: ['tech']
#thumbnailImage: //example.com/image.jpg
---

<!--more-->

How is theme set up? Via git submodule

## How to Update Theme

I was rolling with an older version of my theme for a while.

You can see from below that it was using `$0.4.8-BETA` tag.

```sh
# Within theme folder
personal-website/themes/tranquilpeak (#0.4.8-BETA)
```

Running `git tag`, we can see the tag we are on is 4 releases behind the current one.

```sh
λ  g tag           
0.1.0-ALPHA
...
0.4.8-BETA
0.5.0-BETA
0.5.1-BETA
0.5.2-BETA
0.5.3-BETA
```

So how can we update it? Remember, this is a git submodule. So we can simply run `git checkout <tag>` to switch to our desired tag.

Initially, I went straight to the latest tag and ran `hugo server -Dwv` and saw several errors:

- Missing icons
- Missing pictures

So I had to do the release one step at a time and checking against the [Releases page](https://github.com/kakawait/hugo-tranquilpeak-theme/releases). Going through this process led me to a realization:

- Reading through the releases educates you about additional improvements that have been made that you can take advantage of via small changes to your code
    - These changes can be in the direct tool or underlying packages it is using. In this case there were updates to Font Awesome v5 which led to icon changes, changes to table of contents due to Hugo's markdown engine changes, etc.
- Test each release separately and catch its changes in corresponding commits. We can always rebase later to rename and squash commits to get our final result.
- Making small changes keeps it simple for you to track what is going on and at what point.

So what does the process look like?

1. Run hugo locally via `hugo server -Dvw`, ideally in a separate terminal and open your blog.
1. Navigate to theme folder and check out the next release via `git checkout <tag>`.
1. Look at your blog for any obvious breaking changes - images, icons, text not loading, broken links, etc. Admittedly this process is not very thorough and doesn't guarantee that everything will work. I hope to improve this somehow in the near future.
    1. Debug any issues that come up by comparing against previous version (yes, this will require checking out the previous tag), reading up on the list of changes within the releases page and some trial and error.

NOTE: The most interesting issue came from a coverImage not loading properly for one of my articles. Comparing the respective versions (#0.5.1-BETA vs #0.5.0-BETA) led to no obvious changes that would have led to a broken cover image. I found the fix by searching the theme repo for any mentions of `coverImage` and seeing how it was used in the exampleSite.

The difference was in the example site, they didn't include `https:`, but everything that came afterwards. This minor change got my cover image loading again 🎉 and I was unblocked!

Once its working, commit and push. Changes to the `themes/<theme-name>` will be included.

And voila! That's how you update to newer versions of your desired theme!
