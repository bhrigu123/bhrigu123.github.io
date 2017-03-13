---
layout: post
title: "Instant-Lyrics: New project"
description: "Created a python app that shows lyrics of currently playing spotify song instantly"
date: 2017-03-13 17:48:01 +0530
comments: true
categories: python
---

I love listening to music on Spotify. There were times I used to wish that I could instantly view lyrics of the song being played on Spotify, without going through the trouble of browsing the net. Well, not anymore. <!-- more -->


I've created a python application that allows me to do so. It can pick up the currently playing Spotify song details, scrape the lyrics from the internet, and display it to you nicely in a separate window. All this in just one click. It's called [Instant-Lyrics](http://bhrigu.me/Instant-Lyrics).


It's easy to install and get the app running. Check it out.


![Screenshot](https://cloud.githubusercontent.com/assets/6123105/23824316/3fe58044-069a-11e7-804e-180ea4041002.jpeg)


My brother had worked on a similar project ([SpotifyLyrics](https://github.com/yask123/SpotifyLyrics)). But that app was only for Mac users, and I work on Linux. I wanted to create an app that could run on any Linux distro/flavor. Plus, I added other features like fetching the lyrics of any entered song. I added threading such that the lyrics window gets opened instantly, while the app fetches for lyrics in a separate thread.


I used Python Gtk+3 to implement GUIs. Gtk+ can work on any UNIX-like platforms, Windows, and OSX.


I've tested the app on several Linux distros/flavors like Ubuntu, Elementary OS, Arch Linux and Kubuntu. I'm planning to get the app running on OSX also.


Quick Links:

* [Project page](http://bhrigu.me/Instant-Lyrics)

* [GitHub Repo](https://github.com/bhrigu123/Instant-Lyrics)