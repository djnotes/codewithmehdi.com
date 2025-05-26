---
layout: post
title:  "Create Kotlin Multiplatform Apps"
date:   2025-05-26 15:40:00 +0300
categories: development
---

# Create Kotlin Multiplatform Desktop Apps 

## Requirements:
- IntelliJ IDE version 2025.5.1.1 and above
- JDK 21 and above
- Kotlin Multiplatform plugin on macOS and Compose Multiplatform on Windows/Linux

*Note*: At the time of this writing, May 26 2025, Kotlin Multiplatform is only available for macOS. So, we will create the project in IntelliJ on macOS and then we can also build it on the other platforms using Compose Multiplatform plugin. 
here are the steps that need to be taken to create and build a Kotlin Multiplatform app:

## Create a new project
There are two ways to create a KMP project:
- Using the New Wizard in IntelliJ and then choosing Kotlin Multiplatform (Kotlin Multiplatform plugin needs to be installed)
- Using JetBrains KMP web wizard: kmp.jetbrains.com to define the project and then download the project zip for local development

## New Project Wizard in IntelliJ
Press File->New Project and then choose Kotlin Multiplatform on the left. On the right, choose the platforms you target, e.g. Desktop. iOS, Android, etc. I only choose Desktop because we focus on Desktop apps. 

## Building on macOS
To build the the app on macOS, use the default task defined by the project (desktopApp in the list of Run configurations). 

## Building on Windows
Once you installed a JDK version 21 and above, specify the jdk path in the gradle configuration. You can install various JDK versions using winget in Windows Terminal. Note that Gradle prefers forward slash for paths, rather than Windows' "\"" separator. So, change the path accordingly. For example, in my case it is:  

```
org.gradle.java.home=C:/Program Files/Eclipse Adoptium/jdk-21.0.7.6-hotspot
```

## Building distributable packages
To build distributed packages like dmg (on mac), msi (Windows) and flatpak (Linux), run the following gradle command:

```
./gradlew packageDistributionForCurrentOS

# on Windows run: ./gradlew.bat packageDistributionForCurrentOS
```




