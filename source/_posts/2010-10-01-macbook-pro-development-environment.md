---
title: MacBook Pro Development Environment
author: Bennett Smith
layout: post
date: 2010-10-01 08:00
permalink: /2010/10/macbook-pro-development-environment/
categories:
  - Apple
  - Blog
  - How To
  - Security
  - Tips from the Trenches
  - Tools I Use
tags:
  - django
  - django-nonrel
  - gae
  - google app engine
  - python
---
This article covers the steps I went through to setup my MacBook Pro for Google App Engine (GAE) development. I am using the Python runtime in GAE so the focus here is on a Python development environment. 

# Python

## Setting Python 2.5 as Default

My MacBook Pro is running Snow Leopard. I am planning to host my projects on Google App Engine and it requires Python 2.5. Snow Leopard ships with Python 2.6 as the default. You can switch to Python 2.5 using a few simple commands, as follows:

<pre>$ defaults write com.apple.versioner.python Version 2.5
$ sudo defaults write /Library/Preferences/com.apple.versioner.python Version 2.5
</pre>

After issuing these commands you should logout and login, launch a Terminal window and issue the command

<pre>$ python --version
</pre>

It should report <tt>Python 2.5.4</tt> as the result. If it still says <tt>Python 2.6.1</tt> then your change did not take effect. To troubleshoot the problem start with <tt>man python</tt>. It includes information on how to switch the default version of Python on your system.

## Additional Python Modules

Google App Engine expects that the ssl module is installed. This is so it can verify the identity of the GAE servers when trying to deploy your projects. Install it like this:

<pre>$ curl http://pypi.python.org/packages/source/s/ssl/ssl-1.15.tar.gz --output ssl-1.15.tar.gz
$ tar xvf ssl-1.15.tar.gz
$ cd ssl-1.15
$ sudo python setup.py install
</pre>

If you want to use the GAE image manipulation classes while running on the local development server you will need to install PIL using the following command.

<pre>$ sudo easy_install pil
</pre>

The following will be necessary for building some other python libraries later in the process.

<pre>$ sudo easy_install docutils
</pre>

The following modules are necessary if you choose to install IPython (see next section). If you are planning on skipping the IPython installation these can be skipped as well.

<pre>$ sudo easy_install readline
$ sudo easy_install nose
$ sudo easy_install pexpect
</pre>

## IPython

The IPython interactive interpreter is a good addition to your Python development environment. It does not come pre-installed on Snow Leopard. You can download the latest stable version using this command:

<pre>$ curl http://ipython.scipy.org/dist/0.10/ipython-0.10.tar.gz --output ipython-0.10.tar.gz
$ tar -xzf ipython-0.10.tar.gz
$ cd ipython
$ sudo python setup.py install
</pre>

# Google App Engine SDK

The Google App Engine SDK for Python is available at http://code.google.com/appengine/downloads.html. As of this writing you can use the following command to grab the latest version:

<pre>$ curl http://googleappengine.googlecode.com/files/GoogleAppEngineLauncher-1.3.7.dmg --output GoogleAppEngineLauncher-1.3.7.dmg
</pre>

Once you download the <tt>dmg</tt> file open it in Finder and run the installer. It will place all of the necessary files on your machine. Once complete locate the *GoogleAppEngineLauncher.app* icon in Finder and double-click on it. This application provides a nice UI for managing your GAE projects.

# Source Code Management Tools

## Git

I am planning on managing the source code for my projects with <tt>git</tt> and will store my master repositories on <http://github.com>. Apple does not include a copy of <tt>git</tt> on the machine by default. An installer is available at <http://help.github.com/mac-git-installation/>. While you are at it also create an account on github if you don’t already have one. It is useful for *social coding* in the wider open-source community.

## Mercurial

Some of the Django open source software I plan on using is maintained using a distributed source control management tool called Mercurial. An installer for this is available at <http://mercurial.selenic.com>. Download and install the software.

<pre>$ curl http://mercurial.selenic.com/release/mercurial-1.6.3.tar.gz --output mercurial-1.6.3.tar.gz
$ tar xvf mercurial-1.6.3.tar.gz
$ cd mercurial-1.6.3
$ make PREFIX=/System/Library/Frameworks/Python.framework/Versions/2.5 all
$ sudo make PREFIX=/System/Library/Frameworks/Python.framework/Versions/2.5 install
$ hg version
</pre>

# Django-nonrel

I plan on implementing my web applications on top of the Django framework. Some modifications are required in order for this framework to run properly on GAE since Google uses *Big Table* for data storage instead of a relational database. Everything necessary to get Django working in GAE is included as part of the [Django-nonrel][1] project. Specific instructions for GAE are available at <http://www.allbuttonspressed.com/projects/djangoappengine>.

Use the commands listed below to install copies of all the necessary components onto your machine. Everything will be stored in a folder called <tt>DjangoStuff</tt> under your home directory. 

<pre>$ mkdir $HOME/DjangoStuff
$ cd $HOME/DjangoStuff
$ hg clone https://bitbucket.org/wkornewald/django-nonrel
$ hg clone https://bitbucket.org/wkornewald/djangoappengine
$ hg clone https://bitbucket.org/wkornewald/djangotoolbox
$ hg clone https://bitbucket.org/wkornewald/django-dbindexer
$ hg clone https://bitbucket.org/wkornewald/django-testapp
</pre>

Now, pick another folder where you want to setup a practice application. I am calling mine <tt>cs-practice</tt> since this is also the name of my Google App Engine application. 

Use the following commands to configure the practice application for Django-nonrel development.

<pre>$ mkdir $HOME/cs-practice
$ cd $HOME/cs-practice
$ ln -s $HOME/DjangoStuff/django-nonrel/django django
$ ln -s $HOME/DjangoStuff/djangoappengine djangoappengine
$ ln -s $HOME/DjangoStuff/djangotoolbox/djangotoolbox djangotoolbox
$ ln -s $HOME/DjangoStuff/django-dbindexer/dbindexer dbindexer
$ cp -r $HOME/DjangoStuff/django-testapp/* .
</pre>

Once you have the practice folder setup you need to edit the <tt>app.yaml</tt> file and change the application name to reflect the Google App Engine application name you selected when registering on <http://appengine.google.com>.


 [1]: http://www.allbuttonspressed.com/projects/django-nonrel
