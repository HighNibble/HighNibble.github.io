---
title: "Git Wizardry II: Choosing the right wand"
author: Paco
tags:
  - git
  - gui
  - development
---

As I explained in [my previous post]({% post_url 2019-11-07-git-wizardry-i-spells-dont-come-easy %}), it's important for a developer to understand some aspects about Git, to prevent bad things from happening.

The first thing you must understand is that Git is a *distributed* version control system. Instead of having a single repository in a remote server, every developer has their own local copy of the repository. This allows a clear separation between two different tasks:

- Recording your changes to the repository. You use your local repository for this, so there is no interference distracting you from the bug or feature you're working on. You can even be offline!

- Synchronizing changes from/to other developers, and dealing with possible conflicts. This obviously requires a connection to a remote repository, but it can be done at a later time.

Of course, in addition to the local copy of the repository, you have a working directory in your file system, so you can modify the files in the repository using your favorite editor or IDE. (There is a special case where you don't have have a working directory, but ignore that for the moment.)

Enough with the theory. Now, the most important advice if you're a developer using Git:

**When possible, use a GUI client.**

We've only just begun, but you can guess that Git wizardry uses, like everything else in development, a few abstract concepts. GUI clients depict those abstractions in a way that makes day-to-day work much easier.

Git CLI is a powerful wand, no doubt. And there will be times when you'll have to use it, because other clients won't give you all the options you need. But in my experience, even if you are a very skilled wizard, GUI clients are less error-prone.

That said, not every GUI client is the same. You'll find three different categories:

- The best GUI clients show you all the abstractions in their main interface. You should see, at least, the commit graph and the changes in your working directory. Other abstractions, like remote repositories, should be easily accessible too.

- Some GUI clients are more focused on your local changes. This is the case of many IDEs, which include Git functionality (directly or through a plugin) and help you track your changes while you're editing. Some IDEs are able to show, at your request, the commit graph in a separate tab or window.

- Finally, a few GUI clients try to mimic the interface of old, non-distributed version control systems, to draw the attention of developers coming from there. Avoid them at all costs, or you'll pay a very high price. They claim to be very integrated with your operating system interface, which may be true, but you are trying to master Git wizardry, not operating systems. You choose your wand, not the other way around.

Personally, I use a dedicated client to manage all my Git stuff. But sometimes, if the Git spell in my IDE is just one click away, I use it so I don't have to switch windows. ([We developers are lazy](https://wiki.c2.com/?LazinessImpatienceHubris), right?)

In my next post, I will show you how a Git repository records and organizes your changes.

**Git Wizardry**  
[I: Spells don't come easy]({% post_url 2019-11-07-git-wizardry-i-spells-dont-come-easy %})  
II: Choosing the right wand  
[III: The marauder's graph]({% post_url 2020-01-15-git-wizardry-iii-the-marauders-graph %})  
[IV: Working directories and where to find them]({% post_url 2020-03-09-git-wizardry-iv-working directories-and-where-to-find-them %})  
{: .text-center .notice--success}
