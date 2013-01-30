---
title: 'Cookbook: Snow Leopard, RVM, Ruby on Rails'
author: Admin
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

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_69">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F08%2Fcookbook-snow-leopard-rvm-ruby-on-rails%2F&linkname=Cookbook%3A%20Snow%20Leopard%2C%20RVM%2C%20Ruby%20on%20Rails" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F08%2Fcookbook-snow-leopard-rvm-ruby-on-rails%2F&linkname=Cookbook%3A%20Snow%20Leopard%2C%20RVM%2C%20Ruby%20on%20Rails" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F08%2Fcookbook-snow-leopard-rvm-ruby-on-rails%2F&linkname=Cookbook%3A%20Snow%20Leopard%2C%20RVM%2C%20Ruby%20on%20Rails" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>

 [1]: http://www.commonvision.com.au/tag/readline/
 [2]: http://tim.theenchanter.com/2010/01/getting-ruby-to-use-readline-instead-of.html