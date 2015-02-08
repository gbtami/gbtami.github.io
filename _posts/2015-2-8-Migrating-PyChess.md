---
layout: post
title: Migrating PyChess project hosting from Google Code to GitHub
---

[PyChess](http://www.pychess.org) is a free chess client for Linux desktop created by Thomas Dybdahl Ahle.
The project was hosted on Google Code from the beginning and everything was OK for years. But one time they decided to [disable](https://code.google.com/p/support/issues/detail?id=24324) the Updates/Activity tab, and now the replacement hack using Wiki gadgets doesn't work neither. Then they [disabled](http://google-opensource.blogspot.hu/2013/05/a-change-to-google-code-download-service.html) creating new downloads too. All in all Google Code seems an abandoned project for a long while. 

Where to go? Today the two most viable alternative is GitHub and Bitbucket. The arguments:

GitHub

  - Most popular, most visible
  - Has Gists (Gists let you apply version control to shareable code snippets)
  - Issue tracker has labeling
  - No file attachments in issue tracker (except pictures)

Bitbucket

  - Some project we collaborate with or plan to use are on Bitbucket:
      * gbulb - a PEP 3156 event loop based on GLib
      * fatics - an Internet chess server intended to be a free software equivalent for the server that currently runs at freechess.org
      * mekk.fics - a Python access library for FICS (freechess.org). It can be used to write FICS bots and clients in Python
  - Enables file attachments in the issue tracker
  - Far less popular and visible
  - Issue tracker has no labeling

OK, let see how easy to migrate to them!
Importing our code repository was just a few click in both, so this was not a problem. But what about our issues? First I googled a bit to find how others migrated to Bitbucket. I'v got several hits, and the most promising was [this](https://bitbucket.org/equalsraf/leave-googlecode/) one, but unfortunately when I tried it turned out that Google [shut down](https://code.google.com/p/support/wiki/IssueTrackerAPI) the Issue Tracker Data API too. Sigh.

It's funny, but finally I find what I wanted on Google Code! https://code.google.com/p/support-tools/ They started to create an issue converter from Google Code to Bitbucket/GitHub. To Bitbucket it doesn't migrate attachments, but I created my own [clone](https://code.google.com/r/gbtami-googlecode2bitbucket/), and enhanced it to do.

Unfortunately GitHub doesn't has any import/export functionality, just a web API to push new issues and comments to it. The only remaining problem was when I always run into GitHub abuse message:

    You have triggered an abuse detection mechanism and have been temporarily blocked from content creation. Please retry your request again later.

With some [info](https://github.com/octokit/octokit.net/issues/638) from predecessors helped again. So I created my own [clone](https://code.google.com/r/gbtami-googlecode2github/), and enhanced it and fixed some bugs.

Finally the [discussion](https://code.google.com/p/pychess/issues/detail?id=937) about migration showed that contributors prefer GitHub better than Bitbucked, so PyChess now moved to [https://github.com/pychess/pychess](https://github.com/pychess/pychess)
