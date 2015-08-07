---
title: Notes from my Hard Drive Failure
layout: post
date: 2015-05-12 14:05:38 -05:00
comments: true
category : blog
tags : [Mac]

---

Last month, my failing hard drive took up a lot of my attention, but I still managed to keep working, and I made progress on my Rails project, as well. I've written a few drafts over the last few weeks, but I honestly think they can can be combined into one simple post. (I'm pretty anxious to talk about what I'm doing now, rather than my issues from last month!) Still, there are a few things I learned, and a couple tips that might be useful for others, so I'll condense it down to one post.

<!-- more -->

### Signs Of Impending Doom

One day, all of my browser tabs crashed, while I was watching a YouTube video. it seemed like a corruption with Flash, so I removed Flash, and reinstalled it. That seemed to work for a couple of days,  that I started getting the "spinning pizza wheel" that Macs get when they are having problems processing something. I didn't want to update to OS X Yosemite until after I had finished the Tealeaf program but I figured a clean install might help resolve whatever issue is going on. OS X comes with Time Machine, which seems like a really easy and effective way to keep your system backed up, but I’ve never used it. I’ve been using [SuperDuper!](http://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html) to clone my Macs for years. I used to run it nightly, but these days, most of my user files are symlinked to [Dropbox](https://www.dropbox.com) or [Hubic](https://hubic.com/en/), so I run backups a bit less often. I did a full backup, a couple nights in a row, and it failed both times. So, because you can never be too paranoid, I backed up all of the user files and system files that I thought that I would need. Then I did a clean install and upgraded to the newest OS X operating system. 

### Thoughts on OS X Yosemite
Whenever a new release of OSX comes out, I always read [John Siracusa's reviews of the latest version](http://arstechnica.com/author/john-siracusa/) for Ars Technica[^siracusa]. I knew there were some good features, but I wasn't sure how I felt about the new, flatter UI. As it turns out, I really like it, and I wouldn't want to go back to Mavericks. The integration with my iPhone is better than ever, and everything runs really smoothly (now). After I'd installed Yosemite, things seemed to be working. Once again, I thought that I had resolved the issue. but the frequency of the spinning wheel started to increase. Now I knew I had a problem.  Last year, my SATA cable came loose. I wasn't sure if that might be the case, or if I might have a problem with the logic board or hard drive. Unfortunately, my AppleCare warranty had already expired.

### Hard drive, SATA cable, Logic Board, or...?
I've been a big fan of [Smartmontools](https://www.smartmontools.org) for a long time. After using the built-in Disk Utility to repair permissions, check the drive, and do a basic S.M.A.R.T. check, I fired up Smartcl (the main tool in Smartmontool), and it said the disk was passing. But I could clearly tell from the OSX console, that the drive had errors. Fortunately, I heard about a unique tool for Mac, Scannerz.

### Enter Scannerz
[Scannerz](http://scsc-online.com/index.html) is a set of four utilities that can help you determine exactly what is wrong with your computer. Most tools, including Smartmontools, only check the hard drive for errors. With Scannerz, you can check not only the entire drive, but it can also help isolate issues with cables and logic boards. When I bought it, there was a strange issue with the file, and I couldn't download it. It was late at night, so I sent an email, and was getting ready for bed, when I got a reply back, explaining that there had been a server issue, which was resolved. Then, the owner of the company emailed me with a lengthy set of tips on how to interpret the data. This was late at night. I was very impressed with the service.

Now, I don't consider myself much of a 'fixit' kinda guy. Put me in front of a computer, and I'll figure out how everything works, but I've never been one to unscrew my computer and replace things. But armed with the confidence that comes from looking at a [ifixit guide and video](https://www.ifixit.com/Guide/MacBook+Pro+13-Inch+Unibody+Early+2011+Hard+Drive+Replacement/5119), I decided to replace my hard drive. It was easy, and even enjoyable! Best of all, another scan of my new hard drive, with Scannerz, revealed no errors!

Most similar tools are really just a simple GUI layer over Smartmontools. While Smartmoontools and the native Disk Utility said my drive was fine, Scannerz reported several issues. Scannerz is the real deal. If you have a Mac, and wonder if you should get it, go for it. Unless you administer a bunch of Macs, you probably just need the **Scannerz with Phoenix, Performance Probe 2, and FSE-Lite** version. 


### Caskroom
One other gem, which I'd heard of, but never gotten around to trying, was [Caskroom](http://caskroom.io). If you're on OSX and you like Unix tools, you probably already know that Homebrew is an awesome package manager, which lets you download utilities easily. It's one of the first things I install on any new Mac. Caskroom is an extension to Homebrew, which allows you to download regular OSX applications, including Google Chrome, Screenflow, or Fantastical, right from the command line! There's no need to go to the site, download the image, open it, and then unmount the image. Just type in something like this, and you're good to go:

```
brew cask install google-chrome
```

The only downside is that not every application can be downloaded this way, and if you're using a version that is not there, you'll either need to add it, or go do it the old-fashioned way. But...consider the possibilities. If you had to download dozens of apps, you could use a shell script to set up the bulk of them, and then just deal with any errors or missing apps later.


[^siracusa]: Sadly, OSX Yosemite is the final one; the end of an era. <http://arstechnica.com/apple/2015/04/after-fifteen-years-ars-says-goodbye-to-john-siracusas-os-x-reviews/>
