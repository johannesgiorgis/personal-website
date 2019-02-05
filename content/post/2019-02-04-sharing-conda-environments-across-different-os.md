---
title: "Sharing Conda Environments Across Different Operating Systems"
date: 2019-02-04T21:32:53-08:00
draft: false
metaAlignment: center
categories: []
tags: []
#keywords: ['tech']
#thumbnailImage: //example.com/image.jpg
---

Getting conda environments to work across different Operating Systems.

<!--more-->

# Background

Conda environments are supposed to make it easy to manage and share our packages so others can re-produce them. More often than not, the 'others' is you re-creating the same environment on a different system.

I find myself often in such a situation. I have an Ubuntu desktop and a Macbook Pro. I use Github to host my personal blog, projects and course notes. Having come across repos who's code I was unable to run as there was no `requirements.txt` or `environment.yml` file available, I am a big proponent of adding such files to any repos that have code.

# Problem

The problem arises when I face a `ResolvePackageNotFound` error when trying to re-create a conda environment on my Macbook which was originally created on my Ubuntu desktop:


```bash
$ conda env create -f dq_environment.yml
Collecting package metadata: done
Solving environment: failed

ResolvePackageNotFound:
  - libstdcxx-ng==8.2.0=hdf63c60_1
  - matplotlib==3.0.2=py37h5429711_0
  - markupsafe==1.1.0=py37h7b6447c_0
  - zlib==1.2.11=h7b6447c_3
  - pcre==8.42=h439df22_0
  - bzip2==1.0.6=h14c3975_1002
  - gmp==6.1.2=h6c8ec71_1
  - libffi==3.2.1=hd88cf55_4
  - lxml==4.3.0=py37h23eabaa_1000
  - libedit==3.1.20170329=h6b74fdf_2
...
  - yaml==0.1.7=h14c3975_1001
  - sip==4.19.8=py37hf484d3e_0
  - pyzmq==17.1.2=py37h14c3975_0
  - tk==8.6.8=hbc83047_0
  - gstreamer==1.14.0=hb453b48_1

```

The whole point of conda environment YAML files is to specify the packages required for that environment, so that you or anyone else can quickly re-create it. Hitting the above issue definitely undermines this whole promise.

Usually when I faced this issue, I would just use an existing conda environment as most of the time, I was using the usual pandas, numpy, matplotlib, etc packages which another conda environment already had installed. Obviously, this was not a long term strategy and I needed to come up with a better way.

And when there is a will, there is a way!

# Solution 1

After lots of digging around the web, updating conda on both machines and more debugging, I made some progress and wanted to document it. I don't consider this an ideal solution, rather a work around. I'm also calling it 'Solution 1' as I hope to find a better approach and update this post.

**NOTE**: This walks through the situation where you are creating a conda environment YAML file in Ubuntu and trying to re-create the environment on a MacOS device. 

At a high level, here are the steps:

1. Create conda environment YAML file with `--no-builds` flag specified
2. On target machine, copy YAML file and remove offending packages
3. Test that you can successfully re-create your conda environment

### 1. Create Conda Environment YAML File

First, as this [Github Conda Issues Comment] pointed out, build numbers don't match across platforms, so when creating our conda environment YAML file on our host machine, we need to use the `--no-builds` flag:

`conda env export --no-builds > environment_<platform>.yml`

where `<platform>` is whatever Operating System you are running.

After that, we can commit this change and push it to our Github repo.

### 2. Create copy of YAML File and modify on Target Machine

On our secondary machine (MacOS), we can pull the latest changes. We should now have the recently created environment YAML file available. Let's try to create our environment:

```
conda env create -f environment_ubuntu.yml
Collecting package metadata: ...working... done
Solving environment: ...working... failed

ResolvePackageNotFound:
  - libgcc-ng=8.2.0
  - libstdcxx-ng=8.2.0
  - libgfortran-ng=7.3.0
```

On the positive note, the number of packages not found was reduced to 3. On the negative side, we are still unable to re-create our environment file. But we are getting closer!

Let's make a copy of the YAML file and re-name it:

`cp environment_ubuntu.yml environment_macos.yml`

In our newly created MacOS YAML file, remove the 3 offending packages. 

### 3. Test successful creation of Conda environment

We can now successfully create our environment:

```
conda env create -f environment_macos.yml
Collecting package metadata: ...working... done
Solving environment: ...working... done

...

Successfully installed bleach-3.0.2
#
# To activate this environment, use:
# > source activate dq
#
# To deactivate an active environment, use:
# > source deactivate
#
```

Now, we should have 2 environment YAML files reflecting our 2 Operating Systems:

```
ll -tr *yml
-rw-r--r--  1 jawg  staff   3.0K Jan 23 23:36 environment_ubuntu.yml
-rw-r--r--  1 jawg  staff   2.1K Feb  3 18:06 environment_macos.yml
```

We can now commit these changes and our repo will have the environment files. Of course, this means we have to maintain the two files moving forward. There is probably a way to merge only the necessary/common packages and create one YAML file moving forward. I will work towards that solution.

# References

- [Github Conda Issue Thread]
- [Github Anaconda Issues]

[//]: # (References)

[Github Anaconda Issues]: https://github.com/ContinuumIO/anaconda-issues/issues/9480
[Github Conda Issues Comment]: https://github.com/conda/conda/issues/6073#issuecomment-356981567
