---
title: Adding MongoDB to my Mac OS X Snow Leopard Ruby on Rails Environment
author: Bennett Smith
layout: post
date: 2010-11-15 08:00
permalink: /2010/11/adding-mongodb-to-my-mac-os-x-snow-leopard-ruby-on-rails-environment/
categories:
  - Blog
tags:
  - mac os x
  - mongodb
  - RoR
  - ruby on rails
  - Snow Leopard
---
Tonight I wanted to add MongoDB to my Mac OS X Snow Leopard Ruby on Rails Environment. Refer to my [earlier post][1] for details of how I setup my environment. This post assumes your environment is setup according to the instructions found there.

I wrote the following script to handle installation of MongoDB. I decided to grab the pre-built version of MongoDB from the project site and then place the files under the <tt>/usr/local/ror</tt> directory tree.

<pre>#!/bin/bash

# Get and extract a copy of Mongodb
curl http://fastdl.mongodb.org/osx/mongodb-osx-x86_64-1.6.4.tgz > mongodb-osx-x86_64-1.6.4.tgz
tar xvf mongodb-osx-x86_64-1.6.4.tgz

curl http://downloads.mongodb.org/docs/mongodb-docs-2010-09-23.pdf > mongodb-docs-2010-09-23.pdf

# Move files into final locations
(
    cd mongodb-osx-x86_64-1.6.4
    sudo cp -R * /usr/local/ror
    sudo chmod a+r /usr/local/ror/GNU* /usr/local/ror/README* /usr/local/ror/THIRD*
    sudo gem install mongo
)

(
    sudo cp mongodb-docs-2010-09-23.pdf /usr/local/ror/share/doc/mongodb.pdf
    sudo chmod a+r /usr/local/ror/share/doc/mongodb.pdf
)
</pre>

Download the script tarball (<a href="http://wp-media.s3.amazonaws.com/wp-content/uploads/2010/11/mongodb.sh.tar" class="s3-link">mongodb.sh.tar</a>), extract it into a folder like <tt>/tmp</tt> and then run <tt>sh ./mongodb.sh</tt>. This will download the MongoDB binaries and place everything in the <tt>/usr/local/ror</tt> tree. 

One final step. Since you are running on a Mac you might want to check out a cool MongoDB client called MongoHub. You can learn more and download it from the official [site][2].


 [1]: http://www.idevelopsoftware.com/2010/11/setting-up-my-snow-leopard-ruby-1-9-2-ruby-on-rails-3-0-nginx-passenger-development-environment/
 [2]: http://mongohub.todayclose.com/
