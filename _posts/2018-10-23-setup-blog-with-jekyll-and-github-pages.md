---
layout      : post
title       : "Set up your own blog with Jekyll and GitHub Pages"
date        : 2018-10-23 12:36:00
image       : "/assets/images/posts/2018/10-setup-jekyll-cover.jpg"
categories  : Guide
tags        : jekyll github-pages blog
toc         : true
---

# Introduction
Setting up your own blog is a very easy task to do, especially nowadays.
With the help of Jekyll, Ruby, GitHub Pages and TravisCI it really is just a matter of some couple of minutes.
Plus it's totally free!
In this article I will show you step by step how I did set up my own personal blog.
Everything should be pretty straightforward and clear.
Nevertheless, please let me know if you run into problems of any kind.

# Tool Setup
## Git and GitHub
If you want to host your blog via GitHub as a GitHub Page or on a custom domain, you will need to have an account on GitHub and Git installed on your working machine.
Join GitHub by following [this link](https://github.com/).
The latest version of Git is available [here](https://git-scm.com/downloads).

To check whether Git is properly installed, run the following command:

```text
git --version
```

Some source code editors and IDE tools offer a Git integration.
This will make it a little bit easier to work on your blog articles, because you won't need to switch the working tool to commit your changes.
Personally I like to use one single tool which support everything I need to work properly.

## TravisCI
To make use of a fully automated build process on GitHub Pages for more advanced and individual requirements you will need TravisCI.
TravisCI is an online application that is capable of automatically building software.
Please refer to the [official documentation](https://docs.travis-ci.com/user/for-beginners/) for more general information about TravisCI and build processes.
On [this](https://docs.travis-ci.com/user/tutorial) site you will find the necessary steps to link TravisCI to your GitHub account.
Please follow the instructions to the second point.


## Source Code Editor or IDE
You may want to work with a source code editor or IDE with syntax highlighting and other helpful features.
I am using [IntelliJ Ultimate](https://www.jetbrains.com/idea/download/#section=windows) with the Ruby plugin, but [Visual Studio Code](https://code.visualstudio.com/Download) or something similar to this will do the job, too.
Try to choose an editor or IDE with a build-in terminal and syntax highlighting feature for Ruby, HTML, CSS, SCSS, YML and Markdown.
Although it's not a necessity, features like these will make it easier to work on your blog.

## Ruby
In order to get your blog running locally, you'll need to install the programming language Ruby with Devkit included.
I downloaded the latest version for Windows from [here](https://rubyinstaller.org/downloads/).

After the basic installation of Ruby you will be prompted to install the optional Devkit.
You will need the Devkit in order to install Jekyll successfully.
Please choose the third installation option to run the full installation with MINGW development toolchain.

![Ruby Devkit installation](/assets/images/posts/2018/10-setup-jekyll-devkit.png#post-image)

To check whether Ruby is properly installed, run the following commands:

```text
ruby -v
gem -v
ridk version
```

If you are using an IDE that offers Ruby language integration you may want to add the Ruby SDK.
It's purely optional but will add some language related features like code completion, which always is a nice thing to have.
You will only notive this feature in your Gemfile, though.

## Jekyll
Jekyll is a Ruby gem and comes along with a set of commands to easily build a static Jekyll website.
To install Jekyll, just run

```text
gem install bundler jekyll
``` 

in the Command Prompt.
This will install Jekyll along with Bundler.
Bundler tracks and installs all of the Ruby gems and their versions you will use in your blog later.
It will also be used to build your Jekyll website locally.

To check whether Jekyll and Bundler are properly installed, run the following command:

```text
jekyll -v
bundler -v
```

# Initialization
## Setting up a user repository
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

![GitHub user repository settings](/assets/images/posts/2018/10-setup-jekyll-github-pages.png#post-image)

Therefore, GitHub will automatically try to build anything you push on this branch.
Please keep this in mind.
Well, but what if you are working on larger articles or make greater changes to your blog?
Luckily it's possible to create other branches on user repositories for these purposes.
We will see how to even automate the whole process of releasing a new article to a productive environment.

Clone the repository you just have created via HTTPS or SSH.

## Creating a minimal Jekyll site
Now that we have all tools needed and a GitHub user repository to work with it's time to create your blog.

If not already done open your cloned local repository in your Source Code Editor or IDE with an build-in terminal.
Alternatively, navigate with the Command Line tool to it.
To create a new basic Jekyll site you have to run the following command:

```text
jekyll new . --force
```

This command will use the current directory to create the new Jekyll site.
The `--force` parameter is necessary, because the directory is not empty anymore as already being a git repository.
If anything has worked you should read `New jekyll site installed in C:/path/to/repository.github.io.` as the last output.
Yes, this is basically anything you need to set up your first minimal blog!
The given command will set up some basic files and folders along with a minimal gem-based theme to start with.

To build your newly created Jekyll site locally you only have to run the following command:

```text
bundle exec jekyll serve
```

If anything has successfully worked you should get the following output:

```text
Configuration file: C:/path/to/repository.github.io/_config.yml
            Source: C:/path/to/repository.github.io
       Destination: C:/path/to/repository.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 1.924 seconds.
 Auto-regeneration: enabled for 'C:/path/to/repository.github.io'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

With this you now can access your freshly built Jekyll site with some example content by the given server address.
Now is a good time to commit and push your progress on GitHub.
GitHub will automatically build your Jekyll site which can be accessed online by using your GitHub GitHub Pages URL `https://<username>.github.io/`.
Locally and remotely your blog should now look like this:

![Minimal Jekyll site](/assets/images/posts/2018/10-setup-jekyll-first-page.png#post-image)

## Basic structure of a Jekyll site
Okay, we now have a basic scaffold to work with.
Let's look on where to add actual content.
For this we need to understand the directory and file structure of Jekyll.
Your repository should currently look like this:

```text
.
├── _config.yml
├── _posts
|   └── 2018-10-29-welcome-to-jekyll.markdown
├── _site
├── .sass-cache
├── 404.html
├── about.md
├── Gemfile
├── Gemfile.lock
└── index.md
```

But for what are the files and directories used?
* **_config.yml**: Configuration data will be stored here
* **_posts**: This is the directory where blog posts should be stored
* **YYYY-MM-DD-title-of-post.markdown**: Naming convention for any blog post markdown file
* **_site**: The built Jekyll site. Here is everything that is actually displayed in your browser
* **.sass-cache**: Stylesheet cache
* **404.html**: A basic error page
* **about.md**: Information about you
* **Gemfile**: Information about Ruby gems you want to use for your Jekyll site
* **Gemfile.lock**: Snapshot of the current Ruby gems and their versions in use
* **index.md**: Static content on your main page and layout information

Please refer to the [official documentation](https://jekyllrb.com/docs/structure/) of Jekyll for further information on this topic.

In order to get started you probably want to modify the `_config.yml` file.
The most basic information about your blog is stored there.
Go ahead and try to make your first changes there.
After you are done, try to rebuild the Jekyll site to see the changes.

To add a new blog post just add a markdown file in the `_posts` directory according to the existing example markdown file.
Please refer to [this](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf) site for more information about how to style your text with markdown files.
Besides of the content of your article you probably have noticed some kind of head part in the file.
In this head part there are pieces of important meta information on your blog post written.
Jekyll uses them for blog post related adjustments - e.g. what page layout to use for or which categories to associate with this particular blog post.
Basically the meta information section only consists of some variables which are declared and/or used somewhere else in the sourcecode of this repository.
The meta information section of the example blog post markdown file looks like this:

```yaml
layout: post
title:  "Welcome to Jekyll!"
date:   2018-10-29 22:26:13 +0100
categories: jekyll update
```

The `_config.yml` file and `_posts` directory are the two most important things to understand and to use.
Of course, at some point you probably will modify other files, too.
In case you aim to get a very basic blog running, you can stop reading here, because to write articles on your blog it's only necessary to add new blog post markdown files and push your changes to GitHub.

## Themes
The basic Jekyll theme is not bad, but maybe a little bit too plain.
Personally I think it's worth the time to choose or create a blog theme you really like and suits your personal style.
There are a lot of great predefined themes to choose from and some of them are very easy to set up.
However, not all of them are compatible with GitHub Pages right away and therefore won't be displayed on your site.
[Here](https://pages.github.com/themes/) is a list of all Jekyll themes supported by GitHub Pages by default.
If you already like one of these without any further customization, see the usage instructions on the respective theme repository page and you are all set.

Most of the Jekyll themes you will find [here](http://jekyllthemes.org/) won't work with GitHub Pages without using TravisCI.
Same goes to any customization you maybe want to make on your Jekyll site.

# Hosting
## Using Git branches
In order to automatically build your Jekyll site with TravisCI, it's necessary to work at least on two Git branches.
The master branch will only be used to build your blog by GitHub Pages.
You won't work on that branch actively anymore.

A second branch - let's call it "release" - will serve as your new main branch to work on and push your commits to.
So you have to create a new branch that branches off of the master branch.
If you don't know how to do that, please refer to [this](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell#_create_new_branch) site.
From now on you don't have to push anything on the master branch.

## Build your blog with TravisCI
Now it's finally time to use TravisCI to build your blog and push the static files of the built site to your master branch automatically.
To achieve this, firstly you have to follow the instruction steps three to four on [this](https://docs.travis-ci.com/user/tutorial) site you already have visited before.

The `.travis.yml` file should look like this in order to tell TravisCI to pull only from your release branch and push the built site to your master branch.

```yaml
language: ruby

cache: bundler

branches:
  only:
  - release

script:
- JEKYLL_ENV=production bundle exec jekyll build --destination site

deploy:
  provider: pages
  local-dir: ./site
  github-token: $GITHUB_TOKEN
  target-branch: master
  skip-cleanup: true
  keep-history: true
  on:
    branch: release
```

Surely you have noticed the `$GITHUB_TOKEN` variable in my `.travis.yml` file.
It's very important for authentication purposes.
Without it TravisCI is not allowed to pull your repository or push to it.
Please add a new personal access token to GitHub according the instructions you'll find [here](https://docs.travis-ci.com/user/deployment/pages/) and add it as a variable to TravisCI like described [here](https://docs.travis-ci.com/user/environment-variables#defining-variables-in-repository-settings).
The variable name you use there has to be identical to the variable name in your `.travis.yml` file.
    
# Everything else in jekyll doku