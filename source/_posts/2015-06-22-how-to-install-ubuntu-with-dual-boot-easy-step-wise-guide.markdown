---
layout: post
title: "How to install Ubuntu with dual boot (Easy step-wise guide)"
date: 2015-06-22 14:30:32 +0530
description: Step wise guide to Ububtu installation with dual boot.
comments: true
categories: Ubuntu
---
Here is the easy step-wise installation guide to install Ubuntu along side with your Windows (dual boot)

####Step 1: Make sure you have free, unallocated space
Open your Windows, right click on your 'Computer', click on 'Manage', Click on 'Disk Management' <br>
Here you shall see the current partitions of hard disk.<!--more--> **Your computer allows at max of 4 primary partitions only.** So make sure that you have no more than 2 partitions (as Windiows creates a reserved partition known as 'System Reserved', and we will install Ubuntu in the fourth one). <br>
In case you have 3 or more partitions, transfer all files from one partition to another and delete that partition. For eg. , Transfer all files from your E:// Drive to D:// drive, and in the 'Disk Management', right click on the partition corresponding to E:// drive and delete that partition. (such that you only have C:// and D:// drive in your *Computer* (and you will also see *System Reserved* in Disk Managament. So total 3 primary partitions))

*[`Note:` If you have any important files on your PC, you must always back up your data in the proper drive or on another device /drive is possible. You are responsible for any changes being made on the computer, and always read the instructions carefully]*


{% img [diskimg] /images/ubuntu/diskmgmt.jpg 600px 600px [This is how your partitions should look in 'Disk Management' [Disk Management Partitions]] %}
<br> 
The removed space is shown in black as 'Unallocated Space', where we'll install Ubuntu. <br>
(You can also shrink other volumes to create unallocated space, as required. I recommend at least 60 gb of space for Ubuntu, depending upon the type of work you will be doing.)


####Step 2: Download Ubuntu and make a bootable device
Download the latest version of Ubuntu from [here](http://www.ubuntu.com/download/desktop)
<br>
Now, a bootable pen drive is to be made using the downloaded .iso file. Download the software [Universal USB Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/), and follow its instructions to do so. <br>
(Or you can also use [Rufus](https://rufus.akeo.ie/))


####Step 3: Boot the pen drive
Restart your computer and press the Boot Menu Key, to open boot options when the display starts. (Usually it's F12 key) <br>
Select the Pen Drive to boot from it.<br>
When Ubuntu loads, select the option 'Install Ubuntu' and follow the instructions.
Connect to the internet if possibe, and *check* on 'Install Updates while installing' and 'Install Third Party Software' 


####Step 4: Creating Partitions for Ubuntu
When it asks for the type of installation, select 'Something else'.
{% img [diskimg] /images/ubuntu/somethingelse.png 600 800 [Select 'Something else' [Installation type]] %}

Now you would see the partitions of your disk as: <br>
{% img [diskimg] /images/ubuntu/partitions.jpeg 500 500 [[partitions]] %} <br>
In this image, sda1, sda2 and sda4 are the current partitions of the disk, and **free space** is the unallocated space. <br>
(If you see *unusable space* instead of *free space*, that means your computer already has 4 primary partitions, and you will need to delete one of the partition. Partition could be deleted from here also by selecting that partition and clicking on the minus '-' sign below (but data in that drive will be lost. Therefore, open windows, back up your data, and delete partition from there) )

Select the *free space*, click on '+' to create a partition for the root folder as: <br>
{% img [diskimg] /images/ubuntu/createpart.png 500px 500px [Create root destination [Create root destination]] %} <br>
Here, 20gb is being allocated for your workspace in Ubuntu. I recommend around 50-100 GB (depending on the work you will be doing.)

Select *free space* and Click on '+' again to create 'Swap Area' as: <br>
*If you have less than 4GB of RAM, select the size of swap area equal to your RAM, else select 4GB. Since I have 4GB RAM, I'll select 4096 MB for Swap Area* <br>
{% img [diskimg] /images/ubuntu/swaparea.jpeg 500px 500px [[Create Swap Area]] %} <br>

Create another partition for 'Boot' of 512 MB as:
{% img [diskimg] /images/ubuntu/newboot.jpg 500px 500px [[Create Boot Area]] %}

Now you have successfully created your partitions. The root directory *'/'* is where Ubuntu will be installed, and where you will save your files. Proceed and Confirm *'Write Changes to Disk'*.

Follow rest of the instructions to fill up your basic details, and continue with the installation. You will see the installation bar which takes a few minutes, and later will ask you to restart your computer.


####Step 5: Installation Complete
When installation completes and the computer restarts, you will be asked to select an OS to boot. <br>
{% img [diskimg] /images/ubuntu/ubuntuboot.jpg 500px 500px [[Select OS]] %} <br>
The first option will launch Ubuntu.
The last *Windows loader* option will launch you Windows, like it used to before.

So I hope this tutorial was helpful to you, and you could install Ubuntu without any trouble. <br>
Comment here if you still have any doubts or problems, or for your feedback.
 







