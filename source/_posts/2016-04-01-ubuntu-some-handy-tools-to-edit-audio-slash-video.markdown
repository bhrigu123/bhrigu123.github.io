---
layout: post
title: "Ubuntu | Linux: Some handy tools to edit audio, video and images"
date: 2016-04-01 19:56:20 +0530
comments: true
categories: Ubuntu, Linux
---

<center>
	{% img [erimg] /images/ubuntutools/ubuntu.jpg Ubuntu %}
</center><br>

There are several tools & libraries to edit audio/video files in Linux, such as change dimensions, video converter, resize/rotate images etc.<br>
Mainly we'll use avconv, which can be used as command line in __Linux__.
<!-- more -->

### 1. Resize / Rotate images
In __Ubuntu__, use **nautilus-image-converter**. It adds 2 new menu items, when you right click an image: resize and rotate. To install, run the command on your terminal:

`sudo apt-get install nautilus-image-converter`

Restart nautilus by running `nautilus -q` , and open your file browser. Right click on an image to see options for Resizing and Rotating.
<center>
	{% img [erimg] /images/ubuntutools/resize.png Resize,Rotate images %}
</center><br>
You can even resize multiple images by selecting those images, right click and Resize.
<hr>

### 2. Trim / cut an audio or video
Use a command line tool `avconv` to trim audio/video. Install as:

`sudo apt-get install libav-tools`

To trim an audio/video run the command

`avconv -i srcFileName -c:a copy -c:v copy -ss 00:03:40 -t 00:01:12 targetFileName`

Time parameter is given in format hh:mm:ss <br>
The first time parameter is the start time. The second time parameter is the **duration** of the clip that you want from the start time. (*not the end time*)

<hr>
### 3. Change video resolution
Again `avconv` is used for this. (install as stated above)

For eg. to change resolution of a video to __640x480__, run the command

`avconv -i video.mp4 -s 640x480 output.mp4`



*[Note]: If the above command doesn't run and gives you a warning to run with -strict -2, Run the command as `avconv -i video.mp4 -s 640x480 -strict -2 output.mp4`*
 

<hr>
### 4. Change video format
Using avconv to change format of a video, for eg, from `mov` to `mp4`. (install as stated above)

`avconv -i video.mov -strict -2 output.mp4`

<hr>
### 5. Extract audio from Video file
Using avconv, run the command

`avconv -i video.mp4 -vn -f mp3 sound.mp3`