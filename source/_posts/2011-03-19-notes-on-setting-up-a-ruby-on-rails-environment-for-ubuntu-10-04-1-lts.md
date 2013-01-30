---
title: Notes on setting up a Ruby on Rails Environment for Ubuntu 10.04.1 LTS
author: Admin
layout: post
permalink: /2011/03/notes-on-setting-up-a-ruby-on-rails-environment-for-ubuntu-10-04-1-lts/
categories:
  - Blog
---
Clone virtual machine

Boot up, open terminal window and run the following commands in order to configure network. (Updates the MAC address for the virtual network adapter.)

<pre># rm -fr /etc/udev/rules.d/70-persistent-net.rules
# shutdown -r now
</pre>

Packages to install…

<pre>sudo apt-get install vim
sudo apt-get install build-essential
sudo apt-get install curl
sudo apt-get install zlib1g-dev
sudo apt-get install libssl-dev
sudo apt-get install libreadline5-dev
sudo apt-get install sqlite3 libsqlite3-dev sqlite3-doc
sudo apt-get install libxml2 libxml2-dev libxslt1-dev
sudo apt-get install libyaml-dev
sudo apt-get install postgresql-8.4 postgresql-client  postgresql-client-8.4 postgresql-doc-8.4
sudo apt-get install postgresql-server-dev-8.4
sudo apt-get install pgadmin3
sudo apt-get install libcurl4-openssl-dev
sudo apt-get install git-arch git-doc git-csv git-svn git-email git-daemon-run git-gui gitk gitweb
sudo apt-get install ssh subversion libgssapi-perl libio-socket-inet6-perl rssh molly-guard
sudo apt-get install openssh-blacklist openssh-blacklist-extra socklog-run
sudo apt-get install rdist makejail subversion-tools db4.8-util

sudo apt-get install autoconf autoconf2.13 autoconf-archive gnu-standards autoconf-doc libtool gettext gettext-doc libtool-doc

sudo apt-get install ruby
sudo apt-get install ruby1.8 ruby1.8-dev rubygems1.8 ruby1.8-examples ri1.8 rubygems-doc graphviz graphviz-doc

sudo apt-get install flex bison bison-doc
</pre>

Setting up RVM

<pre># System Wide RVM Installation
bash &lt; &lt;( curl -L http://bit.ly/rvm-install-system-wide )

# Setup of user defaults
edit /etc/adduser.conf
 - enable the EXTRA_GROUPS stuff and make sure the user is added to the 'rvm' group
edit /etc/skel/.bashrc to add the necessary RVM initialization stuff

sudo su -
rvm install ruby-1.9.2-p0

rvm install ruby-1.9.2-head
</pre>

(notes on config of Postgres on Ubuntu https://help.ubuntu.com/community/PostgreSQL)

<pre>curl ftp://ftp.ruby-lang.org:21//pub/ruby/1.9/ruby-1.9.2-p0.tar.gz > ruby-1.9.2-p0.tar.gz
tar xvf ruby-1.9.2-p0.tar.gz

cd ruby-1.9.2-p0
./configure --prefix=/usr/local/ror --enable-shared
make
make test
sudo make install
</pre>

Create a file called /usr/local/ror/ror_env.sh. Add the following to it:

<pre>export PATH=/usr/local/ror/bin:$PATH
</pre>

Run the command

<pre>sudo ln -s /usr/local/ror/ror_env.sh /etc/profile.d/ror_env.sh
</pre>

Log out / Log in

Open a terminal window

<pre>$ which ruby
/usr/local/ror/bin/ruby
$ which gem
/usr/local/ror/bin/gem
</pre>

<pre>sudo su -
gem update --system
gem install rails -v 3.0.3
gem install sqlite3-ruby
gem install pg
gem install passenger
</pre>

<pre>passenger-install-nginx-module --prefix=/usr/local/ror --auto-download --auto
</pre>

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_66">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F03%2Fnotes-on-setting-up-a-ruby-on-rails-environment-for-ubuntu-10-04-1-lts%2F&linkname=Notes%20on%20setting%20up%20a%20Ruby%20on%20Rails%20Environment%20for%20Ubuntu%2010.04.1%20LTS" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F03%2Fnotes-on-setting-up-a-ruby-on-rails-environment-for-ubuntu-10-04-1-lts%2F&linkname=Notes%20on%20setting%20up%20a%20Ruby%20on%20Rails%20Environment%20for%20Ubuntu%2010.04.1%20LTS" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2011%2F03%2Fnotes-on-setting-up-a-ruby-on-rails-environment-for-ubuntu-10-04-1-lts%2F&linkname=Notes%20on%20setting%20up%20a%20Ruby%20on%20Rails%20Environment%20for%20Ubuntu%2010.04.1%20LTS" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>