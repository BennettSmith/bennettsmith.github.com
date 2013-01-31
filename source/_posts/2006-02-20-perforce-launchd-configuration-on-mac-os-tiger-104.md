---
title: Perforce launchd configuration on Mac OS Tiger (10.4)
author: Bennett Smith
layout: post
date: 2006-02-20 08:00
permalink: /2006/02/perforce-launchd-configuration-on-mac-os-tiger-104/
categories:
  - SCM Tools
  - Software
---
Mac OS Tiger introduced a new daemon control application called launchd. This application is supposed to take the place of rc scripts, xinitd scripts, and cron jobs. The launchd process is configured using XML text files that conform to the Apple plist DTD. Perforce does not provide a sample launchd configuration file for the p4d daemon.

The following is an example of how I configured p4d to run on my Tiger server. Be sure to edit it appropriately for your server configuration.

<pre>&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN"
                        "http://www.apple.com/DTDs/PropertyList-1.0.dtd"&gt;
&lt;plist version="1.0"&gt;
&lt;dict&gt;
	&lt;key&gt;GroupName&lt;/key&gt;
	&lt;string&gt;perforce&lt;/string&gt;
	&lt;key&gt;Label&lt;/key&gt;
	&lt;string&gt;com.perforce.p4d&lt;/string&gt;
	&lt;key&gt;OnDemand&lt;/key&gt;
	&lt;false/&gt;
	&lt;key&gt;Program&lt;/key&gt;
	&lt;string&gt;/usr/local/bin/p4d&lt;/string&gt;
	&lt;key&gt;ProgramArguments&lt;/key&gt;
	&lt;array&gt;
		&lt;string&gt;/usr/local/bin/p4d&lt;/string&gt;
		&lt;string&gt;-r&lt;/string&gt;
		&lt;string&gt;/Depot&lt;/string&gt;
		&lt;string&gt;-p&lt;/string&gt;
		&lt;string&gt;1666&lt;/string&gt;
		&lt;string&gt;-J&lt;/string&gt;
		&lt;string&gt;/Depot/journal&lt;/string&gt;
		&lt;string&gt;-L&lt;/string&gt;
		&lt;string&gt;/Depot/p4err&lt;/string&gt;
	&lt;/array&gt;
	&lt;key&gt;RunAtLoad&lt;/key&gt;
	&lt;true/&gt;
	&lt;key&gt;ServiceDescription&lt;/key&gt;
	&lt;string&gt;Perforce Daemon&lt;/string&gt;
	&lt;key&gt;StandardErrorPath&lt;/key&gt;
	&lt;string&gt;/Depot/p4d.stderr.txt&lt;/string&gt;
	&lt;key&gt;StandardOutPath&lt;/key&gt;
	&lt;string&gt;/Depot/p4d.stdout.txt&lt;/string&gt;
	&lt;key&gt;UserName&lt;/key&gt;
	&lt;string&gt;p4admin&lt;/string&gt;
	&lt;key&gt;WorkingDirectory&lt;/key&gt;
	&lt;string&gt;/Depot&lt;/string&gt;
&lt;/dict&gt;
&lt;/plist&gt;
</pre>

I place this file in the directory /Library/LaunchDaemons, and is named perforce.plist. The permissions look like this:

<pre>-rw-r-----    1 root  wheel   1012 Jan  5 22:21 perforce.plist
</pre>

You will need to tell launchd about the new plist by running:

<pre>$ sudo launchctl load perforce.plist
</pre>

from the /Library/LaunchDaemons directory. To confirm that the new plist has been loaded correctly you can run this command:

<pre>$ sudo launchctl list
</pre>

The list produced should contain a line that says com.perforce.p4d. That is the name given to the new plist for the p4d application.  
At this point you should see a p4d process if you run

<pre>$ ps -aux
</pre>

There should only be one of this process running, and it is the daemon controlling your Perforce server installation.

