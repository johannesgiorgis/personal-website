---
title: "Renaming Files in Linux"
date: 2019-01-23T23:37:26-08:00
draft: false
metaAlignment: center
categories: ['cli tools']
tags: ['tools']
#keywords: ['tech']
---

Simplifying renaming files.

<!--more-->

You navigate to a directory and you find the below staring right back at you:

```
$ ls | wc -l
492
```

```
$ ls
'2020-12-29 hello.csv'  '2021-12-29 goodbye.csv'   '2022-12-29 fsadf.csv'   '2019-01-12 asdfsdf.csv'
'2020-12-29 adsfsdfsd.csv'  '2022-12-29 adsffsfs.csv'   '2022-12-29 afssdfaf.csv'   '2019-01-12 sdfafdssd.csv'
'2022-12-29 dsfafasff.csv'  '2022-12-29 gfhhgkxc.csv'   '2022-12-29 xcijvxcvo.csv'   '2019-01-12 dadfasdf.csv'
```

All 492 files!

Spaces and Linux aren't the best of friends. Especially when your downstream process depends on these files.

How can you fix this?

Well, I would jump to using something along the lines of:

```
for file in $(ls)
do
	new_file=$(echo "$file" | sed 's/ //g')
	mv $file $new_file
done
```

Which would work after some trial and error. But it's always a pain to debug and test this.

But when I recently came across this same situation, I was feeling lazy and turned to my friend Google for help. And Google didn't disappoint! Or rather Stack Overflow didn't!

Thanks to this brilliant [Stack Overflow] post, I discovered the `rename` tool. This [How to Rename Files in Linux] post also provided a good introduction going over how to install it and several command examples.

- Installation
- Example
- Benefits


[//]: # (References)

[Stack Overflow]: https://superuser.com/questions/295994/how-do-i-rename-files-with-spaces-using-the-linux-shell/295997
[How to Rename Files in Linux]: https://linuxize.com/post/how-to-rename-files-in-linux/