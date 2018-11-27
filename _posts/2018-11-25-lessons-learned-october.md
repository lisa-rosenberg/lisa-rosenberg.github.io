---
layout      : post
title       : "Lessons Learned: October 2018"
date        : 2018-11-25
cover       : "/assets/images/posts/lessons-learned-cover.png"
categories  : Lessons-Learned
tags        : lessons-learned c++ jekyll javascript docker scss github-pages
toc         : false
---

![Lessons Learned](/assets/images/posts/lessons-learned-cover.png#post-cover)

Lessons Learned is a known concept in project management.
One can collect knowledge or understanding gained by experiences for personal reflection and future reference.
Articles in this category will contain a short overview about things I have learned or experienced in the past month.

This is what I learned and experienced in October 2018:

## Personal blog
- I learned how to set up a personal blog with the power of Jekyll, Ruby, GitHub, GitHub Pages and Travis CI.
It's very easy to start with and surprisingly simple to fully automate the hosting process.
At the same time it's a very manual and lengthy task to apply your very own structuring and styling ideas.
I wrote a [guide](https://lisa-rosenberg.github.io/guide/2018/10/31/setup-blog-with-jekyll-and-github-pages.html) covering the important steps on how to set up your own blog using Jekyll and GitHub Pages.

- It's possible to host a GitHub Pages website either with a user repository or a project repository.
The main differences are the URL of the website and the branching structure.

- I made myself familiar with the directory and file structure of Jekyll and Ruby.

- New to me was the CSS extension language SCSS - it offers a clearer syntax and better variable usage.
[Here](https://www.rechnerhaus.de/blog/unterschied-zwischen-css-scss-sass) is an example code of CSS and SCSS to make the syntax differences syntax clear.

## Talks
- In October 19th I held my first notable talk on a big internal event of my employer.
With both the preparations for the presentation and the talk itself I learned really a lot.
While working on the presentation I got a clear picture about the important pieces of information I want to share with the attendees and how to do it best.
It helped me a lot with the preparation for every future talk.

- With this I also added a new topic ("How we can inspire kids and teens with IT workshops") to the list of my talks.

## Volunteer work
- Again, I attended a Kids4IT workshop in Hamburg as a mentor.
This time we choose the Calliope mini as the workshop's main topic, which was new to me.
The Calliope mini is a very interesting single-board computer for kids and teens (... and grown-ups, too 😉).
It's a rather cheap gadget that offers a lot of possibilities due to its various sensors and I/O interfaces.

- At the workshop I got the opportunity to initiate an ice-breaker game with the kids and mentors.
This was the first time in my life doing something like this!
The kids and mentors were accepting it very well - leaving me very relieved.
Hopefully we will doing these activities on every workshop from now on.

## Study
- In this semester I attend the course "Computer Graphics".
The goal is to implement a ray tracer in C++ step by step.
Both the programming language and the topic are new to me and very exciting.

- Running the following code will result in the output "this.a".
This is because of the fact that "this" in the context of a function is referencing the global object and therefore overwrite the "a" of the first line.

```javascript {.line-numbers}
var a = "value";

function outerClosure() {
    a = "awesome";
    this.a = function a() {
    }
}

outerClosure();
console.log(a);
```

## Work
- I got to know Docker and its features a lot better in this month.
Right now we are establishing different images to provide the possibility to test every feature branch separately.
It's thrilling to be part of this development!