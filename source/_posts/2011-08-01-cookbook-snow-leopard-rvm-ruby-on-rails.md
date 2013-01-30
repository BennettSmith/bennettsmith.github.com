---
title: 'Cookbook: Snow Leopard, RVM, Ruby on Rails'
author: Bennett Smith
layout: post
permalink: /2011/08/cookbook-snow-leopard-rvm-ruby-on-rails/
categories:
  - Blog
---
Recently I decided to clear out my RVM environments and start fresh. I’m running on a Snow Leopard MacBook Air. Here are the steps I went through. 

<pre>$ curl -O ftp://ftp.cwru.edu/pub/bash/readline-6.0.tar.gz
$ tar xvf readline-6.0.tar.gz
$ cd readline-6.0
$ ./config &#038;&#038; make &#038;&#038; sudo make install
$ cd ..
$ rm -rf $HOME/.rvm
$ bash &lt; &lt;(curl -s https://rvm.beginrescueend.com/install/rvm)
$ rvm install 1.8.7 -C --with-arch=x86_64, --with-readline-dir=/usr/local
$ rvm system
$ rvm gemset export system.gems
$ rvm 1.8.7
$ rvm gemset import system
$ rvm --default 1.8.7
</pre>

The following pages were helpful in figuring this out.

*   [RVM, Mac OSX 10.6 and Ruby 1.8.78 p302 Install Error][1]
*   [getting ruby to use readline instead of libedit][2]


 [1]: http://www.commonvision.com.au/tag/readline/
 [2]: http://tim.theenchanter.com/2010/01/getting-ruby-to-use-readline-instead-of.html
