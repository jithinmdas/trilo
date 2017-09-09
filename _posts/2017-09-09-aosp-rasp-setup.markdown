---
layout: post
title: Getting started with AOSP
date: 2017-09-08 16:00:00
description: How to setup development environment on Linux for AOSP (Android Open Source Project)
---

#### **Hardware requirements**

Minimal requirements needed for your workstation.

1. 64-bit environment
2. At least 100GB of disk space. If you conduct multiple builds you will need more space.
3. At least 4GB of RAM

#### **Software requirements**

You can build Android on Linux or Mac. But I prefer Linux specifically Ubuntu LTS(Long Term Support), because AOSP master branch is developed and tested on Ubuntu LTS. So software requirements are,

1. OS - Ubuntu 12.04/14.04
2. Java Development Kit(JDK) - OpenJDK 7
3. Python 2.7
4. GNU Make 3.82
5. Git 1.7 or newer

### Setting up build environment
<br/>
#### **Installing JDK**

Since we are using Linux, I will give instructions to install the OpenJDK. Install OpenJDK using below commands.
{% highlight bash %}
$ sudo apt-get update
$ sudo apt-get install openjdk-7-jdk
{% endhighlight %}

Update the default Java version by running
{% highlight bash %}
$ sudo update-alternatives --config java
$ sudo update-alternatives --config javac
{% endhighlight %}

#### **Install required packages**
{% highlight bash %}
$ sudo apt-get -y install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib 
$ sudo apt-get -y install libc6-dev-i386 lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache libgl1-mesa-dev libxml2-utils 
$ sudo apt-get -y install xsltproc unzip mtd-utils u-boot-tools lzop liblzo2-2 liblzo2-dev zlib1g-dev liblz-dev uuid uuid-dev
{% endhighlight %}

### Downloading the source
<br/>
#### **Installing Repo**
Repo is a tool which is used to handle a number of Git repositories. Repo is developed for handling the Android Development. 

To install Repo,
1. Make a bin directory in your home directory
{% highlight bash %}
$ mkdir ~/bin
$ PATH=~/bin:$PATH
{% endhighlight %}

2. Download Repo tool and give needed permissions
{% highlight bash %}
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
{% endhighlight %}

3. Initialize repo client
{% highlight bash %}
$ mkdir ~/working_directory
$ cd ~/working_directory/
$ mkdir my_android
$ cd my_android/ 
$ repo init -u https://android.googlesource.com/platform/manifest -b  android-6.0.1_r3
$ repo sync
{% endhighlight %}
repo sync will take some time to execute, because it is downloading whole source of Android OS. It will be nearly 50GB - 60GB. So you can have a tea break. Once the repo sync is executed then you have the Android Source. 
