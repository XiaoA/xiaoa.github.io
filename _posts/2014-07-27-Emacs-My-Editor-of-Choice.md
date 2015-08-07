---
layout: post
title:  "Emacs, My Editor of Choice"
author: "Andrew Buckingham"
date:   2014-07-27 21:32:07
permalink: /blog/2014/07/27/Emacs-My-Editor-of-Choice/
category: blog
tags:
- editors
- emacs
- vim
---

These days, I hear a lot about [Sublime Text] [sublime], the cool new text editor on the block. I've tried it, and it's OK, but I use [Emacs][emacs], and I honestly don't see any reason to switch. I used to use [Vim][vim][^vim], but I switched to Emacs back in 2010, largely because of [org-mode] [org-mode].

Most people I know don't care about text editors, but if you spend any amount of time coding, you'll definitely want to try out different editors and IDEs, to see what works best for you. And you should choose whatever tools you like, and not worry about what other people use.

We're really lucky that we live in a time when there are so many great choices. For me, there's no contest. Emacs wins, hands down. But I understand that it's not the right choice for everyone.

<!-- more -->

Arguments over which editor is best are tired and boring. One of my employees is just staring out in Computer Science, and I recommended that he first consider Vim or Emacs, because they are powerful, free, and they will always be around, as long as computers have keyboards. A few years ago, a lot of people I respect used TextMate. Now, many of them rave about Sublime Text. Ultimately, it doesn't matter what tool you use. But it is a good idea to consider that the tool you use will require a lot of time and energy to learn to use well. And hopefully, you can customize it to your needs. And when it comes to customizability, no editor can match Vim or Emacs (especially Emacs!). While Sublime might be actively developed in another five or ten years, there's no doubt in my mind that Vim and Emacs will. Plus, if he doesn't like either of them, he can always try something else. This [text editor comparison chart on Wikipedia](http://en.wikipedia.org/wiki/Comparison_of_text_editors) is a great place to start.

I gave him a few links to learn about Vim and Emacs. I thought I'd list them here, in case they're helpful for anyone else.

## Vim
Download: [www.vim.org](www.vim.org) (try vimtutor inside vim)

### Videos
* [http://derekwyatt.org/](http://derekwyatt.org/):  Funny, quirky guy, with lots of great demos and tutorial. He really knows Vim!
* [https://www.youtube.com/watch?v=MGmIJyTf8pg](https://www.youtube.com/watch?v=MGmIJyTf8pg): Tim Pope has made a lot of good plugins
* [https://www.youtube.com/watch?v=p6K4iIMlouI](https://www.youtube.com/watch?v=p6K4iIMlouI): Great talk about efficient text editing, by the guy who ported the old Vi editor to Vim.

### Blog Article
* [http://csswizardry.com/2014/06/vim-for-people-who-think-things-like-vim-are-weird-and-hard/](http://csswizardry.com/2014/06/vim-for-people-who-think-things-like-vim-are-weird-and-hard/)

## Emacs 
* Download: [http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/) (try the tutorial inside emacs)
* [http://www.gnu.org/doc/doc.html](http://www.gnu.org/doc/doc.html) emacs help (also in emacs itself)
* [http://www.emacswiki.org/emacs/](http://www.emacswiki.org/emacs/) probably the best place to go for emacs help, other than in the emacs help docs


### Videos
* [http://emacsrocks.com/](http://emacsrocks.com/) A really, really enthusiastic emacs user. These are short videos that show his little discoveries and customizations. He's put out several good packages, like [multiple cursors][mc], which is an Emacs equivalent to one of the most popular Sublime Text features.
* [https://www.youtube.com/user/rpdillon](https://www.youtube.com/user/rpdillon) These are good intro videos.
* [http://orgmode.org](http://orgmode.org) Many people convert to Emacs just for this. I did.
* [http://vimeo.com/timvisher/videos](http://vimeo.com/timvisher/videos) There's something called Vimgolf, where Vim Users try to do tasks with as few keystrokes as possible. This guy uses Emacs, and he does the same challenges in Emacs. More for learning new features and inspiration than a tutorial for new users. 

There are a few starter kits for Emacs, which set more "sensible" defaults for new Emacs users. I've used some of these in the past. I especially like [Prelude]. But after a while, I found it was easier to start over, and either create or "borrow" what I needed. The Emacs community is very friendly and generous. If you have a problem or need help, and can't find an answer within the extensive documentation built into Emacs, check the links I've provided above, or do a quick Google search. The chances are, you'll find at least one solution to your problem, if not several.

Here's a link to my ever-changing Emacs configuration files: [https://github.com/XiaoA/.emacs.d](https://github.com/XiaoA/.emacs.d). If you have a question or problem, let me know. Maybe I'll be able to help.

[org-mode]: http://orgmode.org
[sublime]: http://www.sublimetext.com/
[emacs]: http://www.gnu.org/software/emacs/
[vim]: http://www.vim.org
[^vim]: In fact, I still use it at work, when I log in to the linux servers. Vi/Vim should always be installed on any *nix server, so it's always good to know how to get around. With just a few memorized commands, you can edit effectively in Vim.
[mc]: https://github.com/magnars/multiple-cursors.el
[Prelude]: https://github.com/bbatsov/prelude
