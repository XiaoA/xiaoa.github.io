---
layout: post
title: "Course 2, Quiz 1"
author: "Andrew Buckingham"
date: 2015-03-21 22:17
permalink: /blog/2015/03/21/course-2-quiz-1/
category: blog
tags:

- ruby
- code
- tealeaf
- rails

---

I've completed the first lesson of [Course 2][course 2]. In the pre-course, we followed the classic Ruby on Rails ['Build a Blog'][build a blog] tutorial, which was great, because I did that back in July, but this time, I could open the files, and understand the Ruby syntax. The tutorial uses Rails generators, which *auto-magically* build the pages and tables for you. When you run the code, and the files are set up in seconds, it looks impressive, but it isn't clear to beginners what is happening. By the end of this course, I'll be able to build a Rails project from scratch, without any gimmicks or shortcuts. 

I've spent a lot of time going over the [Rails guides][rails guides], the [Rails API documentation][rails api], and reading blogs and [Stack Overflow][stack overflow] to deepen my understanding. I read a lot of technical writing and documentation at work, and I've learned that the most important thing is to go from an *extensive* understanding to an *intensive* understanding. In other words, the first time you go through the documentation, you're going to be bombarded with information, much of which will not be relevant of perhaps even very easy to digest. But you should get an overall feel of the features and limitations of the product or system. Most imporantly, you should make sure that you can refer to it again, so that when you need that information, you can find it. Unless you have a photographic memory, you're not going to memorize it all in one reading, or even several.

<!-- more -->

Frameworks like Rails provide a lot of shortcuts and powerful features for knowledgeable developers, but they can be hard to understand for beginners. Based on some of the questions and discussions I've seen online, I think a lot of people dive right into Ruby on Rails, without understanding Ruby. Then, they get lost as they follow along with tutorials that help them automatically generate the files they need, complete with the data they need to get started. It seems like a great convenience, but when it's time to customize it, it's suddenly very challenging. That's where I was back in July. Rails conventions make it so easy, that it seems like magic, but it's a very logical process of setting up **models** to manage the data, **viewers** to display the data in ways that humans can understanding, and **controllers** that direct the process. In this course, we're learning to peel back all of the 'Rails magic' and learn how each line of code can be used to build powerful applications. The Tealeaf program starts with Ruby, then moves through Sinatra, and then Rails, which has helped me build a foundation for mastering Rails. In the first lesson, we started working on a new project, which I'll be discussing soon.

I keep my notes, experiments, and source code for each lesson in Emacs [Org-Mode][orgmode] files. Org-Mode's [Babel][babel] feature is a fantastic implementation of [literate programming][literate]; You can write source code, in a variety of languages (hence, the name, "Babel..."), and evaluate the code right inside of the Org-Mode outline file. You can also export ("tangle") the code into separate files, which can be updated via org-mode! Keeping all my work in an org-mode file makes it convenient to study the code, and track my development. For this course, I've started a 'course2-notes.org' outline. I took the quiz in my 'course2-notes.org' file, and exported the quiz to a Gist, which I've embedded into this blog post. While that might seem complicated, it provides me one central location to store all of the content, links, source code, and experiments for each lesson. It's perfect for reviewing the material, and it's really simple to implement. After all, it's all just data...:smile:

Here's the quiz, which I saved a as a [gist][gist], and embedded in this post...

---

{% gist XiaoA/e489f82212e3107a14dc %}

[course 2]: http://www.gotealeaf.com/curriculum#!rails
[build a blog]: http://guides.rubyonrails.org/getting_started.html
[rails guides]: http://guides.rubyonrails.org/index.html
[rails api]: http://api.rubyonrails.org
[stack overflow]: http://stackoverflow.com/search?q=Rails
[orgmode]: http://www.orgmode.org
[babel]: http://orgmode.org/worg/org-contrib/babel/intro.html
[literate]: http://en.wikipedia.org/wiki/Literate_programming
[gist]: https://gist.github.com/XiaoA/e489f82212e3107a14dc#file-tl_course2_quiz1-org
