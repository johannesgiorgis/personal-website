---
title: "Setting Up My Blog"
date: 2019-01-06T22:41:38+01:00
draft: true
categories:
- blog-work
tags:
- hugo
#- tag2
---

This blog post serves to document how I set up my personal website using the static site generator [Hugo]. It includes the steps I took, next steps, enhancement ideas and resources I came across that helped me launch my website.

<!--more-->

<!-- toc -->

# Setup

**Initial setup**: Sunday, January 6th 2019

- Got all the way to step 6. Have a working website with reading time capabilities and a couple of articles.

## 1. Install Hugo

On my Mac, I use brew to install Hugo:

`$ brew install hugo`

and verify the install:

```
$ hugo version
Hugo Static Site Generator v0.53/extended darwin/amd64 BuildDate: unknown
$ which hugo
/usr/local/bin/hugo
$ ll $( which hugo )
lrwxr-xr-x  1 jawg  admin    28B Jan  6 16:10 /usr/local/bin/hugo@ -> ../Cellar/hugo/0.53/bin/hugo
```


## 2. Create New Hugo Site

I create my Hugo site called, '_personal-website_' and initialize the git repository following the [Hugo Quick Start] guide:

```
$ hugo new site personal-website
$ cd personal-website
$ ll
drwxr-xr-x   3 jawg  staff    96B Jan  6 15:43 archetypes/
-rw-r--r--   1 jawg  staff   8.3K Jan  6 18:58 config.toml
drwxr-xr-x   3 jawg  staff    96B Jan  6 15:47 content/
drwxr-xr-x   2 jawg  staff    64B Jan  6 15:43 data/
drwxr-xr-x   2 jawg  staff    64B Jan  6 15:43 layouts/
drwxr-xr-x   2 jawg  staff    64B Jan  6 15:43 static/
drwxr-xr-x   4 jawg  staff   128B Jan  6 16:38 themes/
$ git init
```

I create the initial commit:

```
$ git add .

$ git commit -m 'First commit'
[master (root-commit) c1bfd3b] First commit
 2 files changed, 9 insertions(+)
 create mode 100644 archetypes/default.md
 create mode 100644 config.toml
```

Next, I create the Github repository and added the existing local git repository to it:

```
$ git remote add origin git@github.com:johannesgiorgis/personal-website.git
$ git remote -v
origin	git@github.com:johannesgiorgis/personal-website.git (fetch)
origin	git@github.com:johannesgiorgis/personal-website.git (push)

$ git push -u origin master
...
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

Afterwards I follow the rest of the Hugo Quick Start guide by setting up the '_anande_' theme, running `hugo server -D` and navigating to the respective URL on my web browser to verify it is working.

**Note**

ADD instructions to remove the git submodule 'anande' theme that may have been done as part of the Quick Start Guide.


## 3. Add Theme and Content

I decided to use the [Tranquilpeak theme]. It looks gorgeous and seems to include a ton of features.

Following the Hugo Quick Start guide's example, I add the theme as a submodule and update my `config.toml` configuration file with the name of the theme:

```
$ git submodule add https://github.com/kakawait/hugo-tranquilpeak-theme.git themes/tranquilpeak

$ echo 'theme = "tranquilpeak"' >> config.toml
```

At this point, my `config.toml` configuration file looks like this:

```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "tranquilpeak"
```

To get started, I add some content. I use `post` instead of `posts` for the directory, as the theme seems to only work with the former.

```
$ hugo new post/my-first-post.md

$ cat content/post/my-first-post.md
---
title: "My First Post"
date: 2019-01-06T15:47:19+01:00
draft: true
---

# Welcome!

Hi welcome to my blog :)
```

Finally, I start the Hugo server with the following options:

- `-D`: build drafts
- `-v`: verbose output
- `-w`: watch file system for changes and recreate as needed

```
$ hugo server -D -w -v
```

The initial website looks pretty sparse :(

![Initial Sparse Looking Site](/images/blog_setup/initial_site_sparse_look.png)


It doesn't look anything like the gorgeous [Tranquilpeak theme demo site]:

![Hugo Tranquilpeak Demo Site Screenshot](/images/blog_setup/hugo_tranquilpeak_demo_site_screenshot.png)



## 4. Fix Sparse Site

Let's fix the sparse looking site. First, I need an example site to get started with. Thankfully, Hugo themes tend to come with _exampleSite_ directories which host example site contents for that theme and Tranquilpeak theme also comes with its own.


### A. Set Up Example Site

The [Tranquilpeak exampleSite] is located under the tranquilpeak theme directory:

`/<hugo-site-path>/themes/tranquilpeak/exampleSite`

It contains the necessary files and directories to launch a Hugo website:

```
$ pwd
~/hugo_first_blog/personal-website/themes/tranquilpeak/exampleSite
$ ll -tra
total 32
-rw-r--r--   1 jawg  staff     7B Jan  6 16:38 .gitignore
-rw-r--r--   1 jawg  staff   8.3K Jan  6 16:38 config.toml
drwxr-xr-x   3 jawg  staff    96B Jan  6 16:38 content/
drwxr-xr-x   3 jawg  staff    96B Jan  6 16:38 static/
drwxr-xr-x  24 jawg  staff   768B Jan  6 16:38 ../
drwxr-xr-x   7 jawg  staff   224B Jan  6 17:01 ./
drwxr-xr-x   3 jawg  staff    96B Jan  6 17:01 resources/
```

Navigate to the _exampleSite_ directory and run the Hugo server, which results in an error:

```
$ hugo server
port 1313 already in use, attempting to use an available port
INFO 2019/01/06 17:01:25 No translation bundle found for default language "en-us"
INFO 2019/01/06 17:01:25 Translation func for language en-us not found, use default.
INFO 2019/01/06 17:01:25 i18n not initialized; if you need string translations, check that you have a bundle in /i18n that matches the site language or the default language.
INFO 2019/01/06 17:01:25 Using config file:
Error: Unable to find theme Directory: ~/hugo_first_blog/personal-website/themes/tranquilpeak/exampleSite/themes/hugo-tranquilpeak-theme
```

Hugo is unable to find the theme directory. Updating the exampleSite's `config.toml` configuration file to point to the right directory fixes the issue. Comment out the current '_theme_', and add the below two lines to point to the '_tranquilpeak_' theme directory created earlier (basically referencing its parent's parent directory):

```
themesDir = "../.."
theme = "tranquilpeak"
```

Running `hugo server` works now. Navigate to the respective URL and now we see the following. Much better!

![Hugo Tranquilpeak Example Site Screenshot](/images/blog_setup/hugo_tranquilpeak_example_site.png)


### B. Set Up Own Site based on Example Site

Now that we got the example site working, let's get our own site working.

First, let's copy the `config.toml` configuration file that the example site uses and see what that gets us. Make a backup of our current `config.toml` configuration file under our site directory. Then copy the example site's `config.toml` configuration file to our site directory:

```
$ pwd
~/hugo_first_blog/personal-website/themes/tranquilpeak/exampleSite
$ cp config.toml ../../../
.git/                  archetypes/            content/               layouts/               resources/             themes/
.gitmodules            config.toml            data/                  orig_config.toml_bkup  static/
```

Running the Hugo server and navigating to our web browser, we see the following. Using the theme's `config.toml` file helped fix our website. We are headed in the right direction!

![Initial Good Looking Site](/images/blog_setup/initial_site_good_look.png)


## 5. Customize Our Initial Site

Let's customize the title, copyright information and remove the StackOverflow logo from the sidebar menu via editing the site's `config.toml` file.

![Initial Customized Working Site](/images/blog_setup/initial_site_good_customized_look.png)

Next, we want to over-ride some of the theme's default settings. First, let's make copies of some of the files we want to modify from the theme default.

### Archetypes

Copy the theme archetype files to the site archetypes directory:

```
$ pwd
~/hugo_first_blog/personal-website/archetypes
$ ls
default.md

$ cp ../themes/tranquilpeak/archetypes/* .
$ ls
default.md	page.md		post.md
```

For now, I want to update the default front matter information that is added to newly created posts. Edit the post.md to ensure posts are in draft mode by default, and disable categories, tags, keywords and thumbnail image:

```
---
title: "{{ replace .TranslationBaseName "-" " " | title }}"
date: {{ .Date }}
draft: true
#categories:
#- category
#- subcategory
#tags:
#- tag1
#- tag2
#keywords:
#- tech
#thumbnailImage: //example.com/image.jpg
---

<!--more-->

```

### Sidebar Menu Background Image

I want a more subdued color for the sidebar menu background image. I chose a navy blue background.

Create the `images/` directory under the `static/` directory:
```
$ pwd
~/hugo_first_blog/personal-website/static
$ mkdir images
$ cd images/
```

Download/Move the desired background image file to the `images/` directory. This is also where I created the `blog_setup/` directory to contain all the images you see in this post.

```
$ ll
...
drwxr-xr-x  8 jawg  staff   256B Jan  6 23:43 blog_setup/
-rw-r--r--@ 1 jawg  staff   6.7K Jan  1 17:16 navy_blue.jpg
```

Great. Time to save this working website to our Github repository.


## 6. Additional Features

In this section, I cover adding additional features to my blog.

### Reading Time

Reading time for a blog post is a useful feature that I want to include in my site. I came across several different Hugo based websites which included reading time for their respective blog posts.

After looking at other Hugo themes, lots of trial and error, I found a way to add reading time to my blog posts. In the _tranquilpeak_ theme, the `layouts/partials/post/meta.html` file is responsible for each blog posts's metadata including time stamp and categories.

First, create the `partials/post/` directory under `<site>/layouts/`. Then, make a copy of the `layouts/partials/post/meta.html` file from the theme directory to the newly created equivalent directory under the site directory.

```
$ pwd
~/hugo_first_blog/personal-website/layouts
$ mkdir partials/
$ mkdir partials/post/

$ cd partials/post/
$ cp ../../../themes/tranquilpeak/layouts/partials/post/meta.html .

$ ls
meta.html
```

The original `meta.html` file contains the following:

```
...
{{ if not (eq .Params.showMeta false) }}
  <div class="postShorten-meta post-meta">
    {{ if not (eq .Params.showDate false)  }}
      <time itemprop="datePublished" datetime="{{ .Date.Format "2006-01-02T15:04:05Z07:00" }}">
        {{ partial "internal/date.html" . }}
      </time>
    {{ end }}
    {{ partial "post/category.html" . }}
  </div>
{{ end }}
```

To add Reading Time, I made the following edits:

- add reading time before the list of categories
- wrap categories around an if statement to ensure blogs with no categories had clean end (`1 min` vs. `1 min ·`)

```
...
    <!-- add reading time -->
    <text> &nbsp; · &nbsp; {{ .ReadingTime }} min read</text>

    <!-- add categories if page contains them -->
    {{ if .Params.categories }}
    	<text> &nbsp; · &nbsp; {{ partial "post/category.html" . }} </text>
	{{ end }}
  </div>
{{ end }}
```

Now, the website blog posts include reading time :)

![Website with Reading Time](/images/blog_setup/website_with_reading_time.png)

An enhancement idea is to allow the reading time to be controlled via the config file


# Next Steps

Below are the next steps I need to take to complete this initial launch:

- [ ] Get a domain name and connect it to website
- [ ] Set up Netlify
- [ ] Set up deployment
- [ ] Jupyter Notebook integration

# Enhancement Ideas

Below are a list of enhancement ideas for down the road:

- [ ] Add Article Series capability
- [ ] Allow reading time to be added/removed via config file


# Resources

[Hugo]: https://gohugo.io/
[Hugo Quick Start]: https://gohugo.io/getting-started/quick-start/
[Tranquilpeak theme]: https://themes.gohugo.io/hugo-tranquilpeak-theme/
[Tranquilpeak theme demo site]: https://themes.gohugo.io/theme/hugo-tranquilpeak-theme/
[Tranquilpeak exampleSite]: https://themes.gohugo.io/hugo-tranquilpeak-theme/exampleSite


## Hugo

- [Hugo Install on Mac Discussion](https://discourse.gohugo.io/t/howto-install-hugo-on-mac/768)


## Why Hugo?

- [From Jekyll to Hugo, From Github Pages to Netlify](https://pawelgrzybek.com/from-jekyll-to-hugo-from-github-pages-to-netlify/)
- [Why Hugo?](https://parsiya.net/blog/2016-01-31-why-hugo/)


## Where to deploy?

- [Hugo: Hosting and Deployment](https://gohugo.io/hosting-and-deployment/)
- [Netlify: Github Pages vs Netlify](https://www.netlify.com/github-pages-vs-netlify/)
- [Blog: Netlify instead of Github Pages](https://yihui.name/en/2017/06/netlify-instead-of-github-pages/)
- [Blog: Moving to Netlify](https://javascriptplayground.com/moving-to-netlify/)
- [Blog: Why I like Netlify](https://www.jerriepelser.com/blog/why-i-like-netlify/)
- [Migrating from Github Pages to Netlify: how and why?](http://www.rebeccabarter.com/blog/2017-06-29-website/)


## Deployment

- [Netlify: Step by Step Guide Victor Hugo on Netlify](https://www.netlify.com/blog/2016/09/21/a-step-by-step-guide-victor-hugo-on-netlify/)

# Git

- [StackOverflow: Remove Git Submodule](https://stackoverflow.com/questions/1260748/how-do-i-remove-a-submodule/1260982#1260982)
