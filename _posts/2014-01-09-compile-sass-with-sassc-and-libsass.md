---
layout: post
title: Compile Sass with SassC and Libsass Guide
---

Recently [Foundation](http://foundation.zurb.com/) launched version 5 of their framework. This introduced me to [Libsass](https://github.com/hcatlin/libsass) and [SassC](https://github.com/hcatlin/sassc), a library and wrapper that compiles Sass using C instead of Ruby. The Libsass compiler dramatically reduces compiling times compared to the Ruby compiler. You can run Libsass with  Node.js and other languages as well instead of using the C wrapper.

The following is a quick start on how to compile and run Libsass with the SassC wrapper.

##Tutorial Prerequisites
I’m using CentOS 6 for this tutorial. You may need to use the sudo command before some of the lines if you do not have root access and it complains about your permissions.

I’m going to start in my /var/www directory created by Apache HTTP but you can do this in any directory you prefer. You do not need Apache HTTP for this.

```
cd /var/www
```

##Step 1 – Install Dev Tools
First to compile in Linux you need to install certain Development Tools. Installing the package is the easiest way to make sure you have everything. Without the necessary Development tools you would possibly get an error similar to *make: \*\*\* [libsass] Error 2.*

```
yum groupinstall "Development Tools"
```

##Step 2 – Git Libsass and SassC

If you don’t already have Git installed you can install it quickly:

```
yum install git
```

Now we’ll clone Libsass and SassC.

```
git clone https://github.com/hcatlin/sassc.git
git clone https://github.com/hcatlin/libsass.git
```

##Step 3 – Compile SassC
Before we can compile SassC we need to link it to the libsass library.

```
vi sassc/Makefile
```

Add the following line to the top of the file.

```
export SASS_LIBSASS_PATH=/var/www/libsass
```

Now we can compile SassC.

```
cd sassc
make
```

You can now link the file to the PATH so that you do not need to type the whole path to run SassC.

```
ln -s /var/www/sassc/bin/sassc /usr/bin/sassc
```

##Step 4 – Test SassC
You can now run SassC from any directory. To view the options run the following:

```
sassc -h
```

To compile a scss file and compress it with a source map you would run the following:

```
sassc style.scss -o style.css -t compressed -g
```

Feel free to let me know of any mistakes I may have made if you’re an expert on this topic. My main reason for this article was a lack of tutorials on this subject online.