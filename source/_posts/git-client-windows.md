---
title: Git Client for Windows
tags: Git Windows
date: 2018-03-29 21:05:27
---

# macOS git clients

Sourcetree for Macos allows me to have a window with multiple repositories connected by ssh doing recurrent refresh every 15 minutes. The UI is intuitive and allows complex actions (git flow, interactive rebases) which saves me a substantial amount of time. It is also free, which is impressive enough. It feels smooth, and the bugs have been sparse, in my experience. Even though the SSH experience leaves a bit to be desired, and i do enjoy the 

# Windows git clients

Why i love Sourcetree 1.X:

* It gives me visibility while fetching multiple repositories concurrently (this is by default every 15 mins.)
* I can switch between repositories by tab instead of opening and closing windows.
* Interactive rebase done easy.
* Folder organization its really helpful.
* Git flow compatible.

Sourcetree 2.0 uses a different UI than the original Sourcetree 1.X. This newer UI doesnt feel as intuitive as the original version. I have kept myself on sourcetree 1.9 for now but newer issues have arisen:

* Managing Github 2 factor auth doesnt work.
* The app can get become way sluggish, on occasions.
* Some bugs exists that require reboots of the app.

Therefore i have decided to look for a newer Git client for windows. I will be testing the following apps:

1. Git Kraken (free version)
2. Git Tower (trial)
3. Fork (beta)
4. Sourcetree 2.0
5. GitExtensions

### Git Kraken

https://www.gitkraken.com/

![i](/images/image2.png)

The good:

* The UI is intuitive
* Dark mode looks great!
* Automatically updating is great.
* Automatically creating and adding SSH Keys is handy.

The so so:

* The graph does not seem intuitive at all for me, compared to other git clients.
* Taking physical folders and combining them into a single Project is useful but lacks flexibility.

The bad:

* No UI to manage Interactive Rebases?
* After Navigating over a few repos it can become quite sluggish, even scrolling the graph can become laggy.
* It would be nice to be shown which repos fetched changes and pending pulls or pushes.

### Git Tower

The good:

* Easy integration with Github, Bitbucket, Gitlab.
* The pull request option on the repo is great.

The so so:

* Allows easy integration with multiple git repos, but the UI for Repositories is still buggy (im on beta 2).
* The history requires getting some used to, some issues like unordered commits based on dates dont seem intuitive at all.

![image1](/images/image1.png)

* The UI for tracking branches can be quite confusing when managing many branches.

The bad:

* No dark mode.
* No pending changes shown from the repositories menu.
* No way to stage just one line from the chunk.

### Git Extensions