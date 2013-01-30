---
title: >
  Setting up my Snow Leopard Ruby 1.9.2, Ruby on Rails 3.0, Nginx, Passenger
  development environment
author: Bennett Smith
layout: post
permalink: >
  /2010/11/setting-up-my-snow-leopard-ruby-1-9-2-ruby-on-rails-3-0-nginx-passenger-development-environment/
categories:
  - How To
  - Software
  - Tips from the Trenches
tags:
  - Mac
  - nginx
  - Passenger
  - RoR
  - Ruby 1.9.2
  - Ruby on Rails 3.0
  - Snow Leopard
---
Snow Leopard ships with Ruby 1.8.7 installed and an older version of Ruby Gems. I am planning on doing some projects with Ruby on Rails and wanted to setup a current environment. My requirements were:

*   Ruby 1.9.2
*   Rails 3.0
*   PostgreSQL 9.0
*   Nginx
*   Passenger

You should download and install the Mac version of PostgreSQL 9.0 from the folks at [EnterpriseDB][1]. You will need to register on the site in order to do the download. Be sure to download PostgreSQL 9.0.1, not one of their *Plus* packages. It is a nicely packaged installer for the freely available version of Postgres. 

Once you install this software you should have a file called <tt>pg_env.sh</tt> in the <tt>/Library/PostgreSQL/9.0/</tt> directory. This file should be added to your <tt>/etc/profile</tt>. Here is an example of what mine looks like: 

<pre># System-wide .profile for sh(1)

# This has to be set to something in order for path_helper (below)
# to update it with paths found in the /etc/manpaths.d directory.
MANPATH=/usr/local/share/man; export MANPATH

# Setup the PostgreSQL environment.
. /Library/PostgreSQL/9.0/pg_env.sh

if [ -x /usr/libexec/path_helper ]; then
    eval `/usr/libexec/path_helper -s`
fi

if [ "${BASH-no}" != "no" ]; then
    [ -r /etc/bashrc ] &#038;&#038; . /etc/bashrc
fi
</pre>

Be sure to log out and log back in before continuing with these instructions. This is important to make sure your PostgreSQL environment variables are set properly. 

One of my goals with this setup is to keep everything independent of the default tools that ship with Snow Leopard. To do this I decided that all of my Ruby on Rails setup will be located in the <tt>/usr/local/ror</tt> directory tree. Here is a script I developed to setup my Ruby on Rails development environment. 

<pre>#!/bin/bash

# Get and extract a copy of LibYAML
curl http://pyyaml.org/download/libyaml/yaml-0.1.3.tar.gz > yaml-0.1.3.tar.gz
tar xvf yaml-0.1.3.tar.gz

# Build LibYAML
(
	cd yaml-0.1.3
	./configure
	make
	sudo make install
)

# Get and extract a copy of Ruby 1.9.2
curl ftp://ftp.ruby-lang.org:21//pub/ruby/1.9/ruby-1.9.2-p0.tar.gz > ruby-1.9.2-p0.tar.gz
tar xvf ruby-1.9.2-p0.tar.gz

# Build Ruby 1.9.2
(
	cd ruby-1.9.2-p0
	./configure --prefix=/usr/local/ror --with-arch=x86_64 --enable-shared
	make
	make test
	sudo make install
)

# Update Ruby Gems
sudo gem update --system

# Install Gems
sudo gem install rails
sudo gem install sqlite3-ruby
sudo gem install pg
sudo gem install passenger

# Configure Passenger for Nginx (downloads Nginx and PCRE automatically)
sudo passenger-install-nginx-module --prefix=/usr/local/ror --auto-download --auto
</pre>

<a href="http://wp-media.s3.amazonaws.com/wp-content/uploads/2010/11/doit.sh.tar" class="s3-link">Download the script</a>, un-tar it and place it in any directory you want. I call the script <tt>doit.sh</tt>, but you can name it anything you like. Run the script using the command shown below. 

<pre>$ sh ./doit.sh
</pre>

Once the script completes you need to add <tt>/usr/local/ror/bin</tt> to your path. I did this by editing my <tt>/etc/paths</tt> file. Here is a copy of the file on my machine: 

<pre>usr/local/ror/bin
/usr/local/bin
/usr/bin
/bin
/usr/sbin
/sbin
</pre>

One more logout/login and you are done. Have fun playing with Ruby on Rails on your Mac!


 [1]: http://www.enterprisedb.com/products/download.do
