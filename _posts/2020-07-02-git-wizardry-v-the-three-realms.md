---
title: "Git Wizardry V: The three realms"
author: Paco
tags:
  - git
  - development
---

In [my previous post]({% post_url 2020-03-09-git-wizardry-iv-working directories-and-where-to-find-them %}), I explored the relationship between a Git repository and its working directory.

To manage the changes in the your files, Git defines what I call the three realms:

- The first realm is called the *Working directory* or *Working tree*. It is, plain and simple, the current status of your files in your file system.

- The second realm is called the *Index* or *Staging area*. As its name implies, it is the place where you stage your next commit.

- The third realm is the Git repository itself, or more specifically, the commit pointed by the special reference `HEAD`. As explained in a previous post, this commit represents your current line of work and will be the parent of your next commit.

While the first and the last are usually easy to understand, the staging area is an elusive concept, especially for novice users. What is the purpose of this index? Wouldn't it be easier to create commits directly from the working directory? Well, not always. Sometimes it would, sometimes it wouldn't.

Since software evolves through time, each commit can be thought as a snapshot of the code at a particular moment. But if you take the snapshot directly from the working directory, you may include some things you didn't mean to. Surely you can remember a time when auxiliary files created by your compiler or IDE, some test data or, even worse, the credentials for the production server ended up in the repository. (By the way, if the last one ever happens to you, take into account that simply undoing it with another commit won't do, since the original commit will still be available in the repository. And even rewriting the commit history may not be enough. Contact an expert as soon as you can to completely obliterate the sensitive data.)

The staging area solves this problem. You can carefully prepare your commit, step by step, little by little. No matter how polluted your working directory is, you can add, delete or modify code in the index, one file at a time. Or, if you need it, one line at a time. This is another advantage of using the index: you can stage (or unstage) selected lines within a file. So it is incredibly easy to leave out those embarrassing comments with self reminders, or those logging messages that everybody uses for debugging although nobody admits it. (Unless you are using the wrong wand, like the Git CLI or a client that does not support selective staging, in which case it is incredibly painful.)

Not only you can progressively stage the contents of the index: you *should*. Nothing prevents you from staging all your changes at the same time, and most Git clients even offer you an easy way to do that, effectively converting your index in a snapshot of your working directory. But if you do that, you are missing a precious opportunity to review the changes you want to commit. You would rather spend a few seconds double-checking. Only fools rush in.

By now you may be thinking that, after all, this staging area does not seem such a bad idea. But how is this idea implemented? Where can you find the index? How can you browse its contents? Well, you can't. At least, not directly. Damn. You were starting to see its potential, and now you are questioning it all again.

Let's get back to the big picture. You are dealing with three (possibly) different copies of your project, one for each of the three realms. If your project contains hundreds of files, it would be totally impractical to show the three sets of files at the same time. Instead, Git clients do something much more sensible: they show the differences between them. There are two important sets of differences to consider:

- The differences between the index and the `HEAD` commit show the changes that are going to be a part of the next commit. Remember that your next commit is going to be a snapshot of the index, and the `HEAD` commit is going to be its parent. In other words, this set of differences represent what the difference will be between your next commit and its parent commit.

- The differences between the working directory and the index show the changes that are **not** going to be a part of the next commit. Even if you see that code in your IDE, and you have successfully compiled and tested it, changes that have not been staged to the index will be left out when committing.

Graphical clients usually show two boxes with these two sets, marking different change types (addition, modification, renaming) with different colors and/or symbols. It's a nice way to watch *The Three Realms* in amazing 2D! Showing code differences is the way Git lets you examine the evolution of your project. You can rapidly calculate the set of differences between your working directory and any commit in the repository, or between any two commits.

So you can't still see the contents of the staging area, but you can imagine it is somewhere in the middle of these two sets of differences. Do not get fooled by this representation! I was once teaching Git wizardry to a colleague, and we had this conversation:

"Ok, I think I get it," he said. "After the commit, the staging area ends up empty."  
"No, it does not," I replied.  
"But this box is empty," he frowned, pointing at the differences between the index and the `HEAD` commit.

You may be confused, too. What happens after you actually commit your changes? Since the new commit was created taking a snapshot of the index, and `HEAD` now points to the new commit, that set of differences is obviously empty. But the index is still there, containing all the files in your project. By the way, the working directory is not affected by the commit action either, so the other set of differences (working directory vs. index) will remain exactly the same.

One last thing you should know about committing. If you add sensible comments, it will make things easier for you, and other developers, in the (not so distant) future. It takes much longer to review the project history when half the commits just say 'Fix'. If you are a good developer, and your code is self-explanatory, a short but informative sentence usually will do. If you need to add more details, use the first line of the comment as a title, since this is what most Git clients will show, and then add as many lines as you want expressing your concerns. (Comments can also trigger actions if your Git server is integrated with other systems, for example, for issue tracking. Do not underestimate the power of comments.)

In my next post, I will show you how developers can synchronize their local repositories to effectively work in the same project.

**Git Wizardry**  
[I: Spells don't come easy]({% post_url 2019-11-07-git-wizardry-i-spells-dont-come-easy %})  
[II: Choosing the right wand]({% post_url 2019-12-10-git-wizardry-ii-choosing-the-right-wand %})  
[III: The marauder's graph]({% post_url 2020-01-15-git-wizardry-iii-the-marauders-graph %})  
[IV: Working directories and where to find them]({% post_url 2020-03-09-git-wizardry-iv-working directories-and-where-to-find-them %})  
V: The three realms  
{: .text-center .notice--success}
