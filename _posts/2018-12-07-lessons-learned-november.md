---
layout      : post
title       : "Lessons Learned: November 2018"
date        : 2018-12-07
cover       : "/assets/images/posts/lessons-learned-cover.png"
categories  : Lessons-Learned
tags        : lessons-learned 
toc         : false
---

![Lessons Learned](/assets/images/posts/lessons-learned-cover.png#post-cover)

Lessons Learned is a known concept in project management.
One can collect knowledge or understanding gained by experiences for personal reflection and future reference.
Articles in this category will contain a short overview about things I have learned or experienced in the past month.

This is what I learned and experienced in November 2018:

## Volunteer work
- I attended a new installment of the Kids4IT workshop in Hamburg.
This time with a completely new topic for us all: [VEX Robotics](https://www.vexrobotics.com/).
It was fun to get to know this modularized robot building kit and interesting to see the kids growing a liking to it so fast!

- Again I got the chance to initiate an ice-breaker game with the kids and mentors.
With doing this I'm getting out of my comfort zone a lot (it's really not an easy task for me).
Actually, this is one of the personal reasons why I'm doing this!
The ice-breaker game went well - with one exception.
One kid was very shy and did not want to say anything at all.
I realized it way too late, so maybe the kid got uncomfortable because of this.
I'll try to be more attentive in the future to handle situations like this better!

## Personal blog
- In this month I wrote my first Lessons Learned article for the month before that.
I learned how to write a Lessons Learned article, so to speak! :)

- I added some share buttons on my blog.
While implementing these I now understand them programming-wise.

- While implementing the share buttons I noticed that probably CSS is acting very weird at a simplification of an empty HTML tag.
When refactoring the empty italic format tag in the following code snippet the share buttons will repeat themselves many times on the page.
Right now I don't really know why a sheer code simplification leads to this kind of unexpected impact.

~~~html
<a  href="https://twitter.com/intent/tweet?text={{ page.title }}&url={{ site.url }}{{ site.baseurl }}{{ page.url }}"
            onclick="window.open(this.href, 'pop-up', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;"
            title="Share on Twitter" ><i class="fa-icon fa-twitter share-button"></i></a>
~~~

- Although Markdown supports code block writing by placing triple backticks before and after the code block I had some trouble to get them to work like they should.
Either the syntax highlighting did not work or the code in the snippet was interpreted as actual code.
After some digging I discovered that Kramdown, Jekyll's default Markdown-superset converter, uses a slightly different syntax with tildes instead of backticks to place a code block.
I found the solution and further information on that problem [here](https://github.com/jekyll/jekyll/issues/3724#issuecomment-105170121).
