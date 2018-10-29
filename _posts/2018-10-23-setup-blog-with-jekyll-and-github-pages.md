---
layout: post
title: "Set up your own blog with Jekyll and GitHub Pages"
date: 2018-10-23 12:36:00
image: "/assets/images/posts/2018/10-setup-jekyll-cover.jpg"
categories: Guide
tags: jekyll github-pages blog
---

Setting up your own blog is a very easy task to do, especially nowadays.
With the help of Jekyll, Ruby and GitHub Pages it really is just a matter of some couple of minutes.
Plus it's totally free!
In this article I will show you step by step how I did set up my own personal blog.
Everything should be pretty straightforward and clear.
Nevertheless, please let me know if you run into problems of any kind.

## Tool Setup
### Source Code Editor or IDE
You may want to work with a source code editor or IDE with syntax highlighting and other helpful features.
I am using [IntelliJ Ultimate](https://www.jetbrains.com/idea/download/#section=windows) with the Ruby plugin, but [Visual Studio Code](https://code.visualstudio.com/Download) or something similar to this will do the job, too.
Try to choose an editor or IDE with syntax highlighting feature for Ruby, HTML, CSS, SCSS, YML and Markdown.
Although it's not a necessity, features like this one will make it easier to work on your blog.

### Git and GitHub
If you want to host your blog via GitHub as a GitHub Page or on a custom domain, you will need to have an account on GitHub and Git installed on your working machine.
Join GitHub by following [this link](https://github.com/).
The latest version of Git is available [here](https://git-scm.com/downloads).

To check whether Git is properly installed, run the following command:
```shell
git --version
```

Some source code editors and IDE tools offer a Git integration.
This will make it a little bit easier to work on your blog articles, because you won't need to switch the working tool to commit your changes.
Personally I like to use one single tool which support everything I need to work properly.

### Ruby
In order to get your blog running locally, you'll need to install the programming language Ruby with Devkit included.
I downloaded the latest version for Windows from [here](https://rubyinstaller.org/downloads/).

After the basic installation of Ruby you will be prompted to install the optional Devkit.
You will need the Devkit in order to install Jekyll successfully.
Please choose the third installation option to run the full installation with MINGW development toolchain.

![Ruby Devkit installation](../assets/images/posts/2018/10-setup-jekyll-devkit.png)

To check whether Ruby is properly installed, run the following command:

```shell
ruby -v
gem -v
ridk version
```

### Jekyll
Jekyll is a Ruby gem and comes along with a set of commands to easily build a static Jekyll website.
To install Jekyll, just run

```shell
gem install bundler jekyll
``` 

in the Command Prompt.
This will install Jekyll along with Bundler.
Bundler tracks and installs all of the Ruby gems and their versions you will use in your blog later.
It will also be used to build your Jekyll website locally.

To check whether Jekyll and Bundler are properly installed, run the following command:

```shell
jekyll -v
bundler -v
```

## Initialization
### Setting up a user repository
Firstly you need to create a new repository on GitHub.
The name for your repository has to follow a certain naming convention in order to make it a GitHub Pages repository: `<username>.github.io`.
GitHub will recognize this as your personal GitHub Page.
The enforced naming convention also leads to a single GitHub Pages domain per user.

A repository with this name is a so called user repository.
Other repositories are normal project repositories.
It's possible to use a project repository instead of a user repository for your Jekyll blog.
 In this article I will focus only on the latter, though.

There is one important restriction regarding user repositories.
In a user repository your GitHub Pages blog will only build from the master branch.
There is no way to change this behaviour in the repository settings:

![GitHub user repository settings](../assets/images/posts/2018/10-setup-jekyll-github-pages.png)

Therefore, GitHub will automatically try to build anything you push on this branch.
Please keep this in mind.
Well, but what if you are working on larger articles or make greater changes to your blog?
Luckily it's possible to create other branches on user repositories for these purposes.
We will see how to even automate the whole process of releasing a new article to a productive environment.

## Hosting
    - Github Pages
    - Travis CI

## Jekyll Basics
    - Folders
    - Files
    
## Everything else in jekyll doku