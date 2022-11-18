---
layout: post
title: "How to Switch Android Studio from JetBrains Toolbox version to Standalone Version"
date: 2022-11-18 
categories: Programming
---

# Is this important

In case you have been using JetBrains Toolbox happily and enjoying it so far, you should probably skip reading this article.
Otherwise, if you tried the toolbox and liked your old days of using the IDE and updating it inside the IDE - NOT THROUGH TOOLBOX - then you are in good company.

# What is the problem?

Imagine you have a few versions of Android Studio installed and managed by JB Toolbox. Now, you want to get rid of the toolbox but keep the IDEs, at least a stable version 
and a preview version. These software are usually installed in a location like `/target/folder/apps/AndroidStudio/ch-x/xx.xxxx.xx.xxxx.xxxxxxx`. You want to install updates to the IDE from inside the IDE, but when you check for updates, a notice says "Updates are managed by JetBrains Toolbox". A simple solution seems to delete the IDE altogether and install a new updated version from Android Studio's website, rather than trying to patch existing version to the latest version. I wrote this article to show it is not required.

# Solution?
Yes, solution! Simply, move the folder of Android Studio i.e. `/target/folder/apps/AndroidStudio/ch-x/xx.xxxx.xx.xxxx.xxxxxxx` to a new path different from the Toolbox path. For example, I moved it to `/target/folder/android-studio-preview`. Then I launched Android Studio from the new path `/target/folder/android-studio-preview/bin/studio.sh` and checked for updates. No more notices of that kind! You are now shown an **UPDATE NOTICE** allowing you to patch the IDE to the latest version.

# Conclusion
JetBrains Toolbox might be great for some people. But, I didn't like it. I prefer to install and manage my Android Studio versions (at most 2) manually. 
This article shows you how to convert your existing AS version installed throught Toolbox to a manually-managed version.
Hope this helps.



# Update 1
The patch was downloaded, but failed to be applied! So, I have to download and install the new version manually :( That's the cost of not liking JB Toolbox and preferring the manual path. Still, I don't give up and persist, because JB Toolbox used to completely download the new version instead of patching it more than often.
