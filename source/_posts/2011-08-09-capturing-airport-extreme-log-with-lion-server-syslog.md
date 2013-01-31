---
title: Capturing AirPort Extreme Log with Lion Server Syslog
author: Bennett Smith
layout: post
date: 2011-08-09 08:00
permalink: /2011/08/capturing-airport-extreme-log-with-lion-server-syslog/
categories:
  - Apple
  - Blog
  - Hardware
  - How To
  - System Administration
---
Mac OS X Lion Server can be used as a syslog server to capture the log messages from an Apple AirPort Extreme wireless router. The instructions below walk you through setting this up.

Syslog is controlled by a plist file found in the launch daemons directory. The full path to the file is:

<pre>/System/Library/LaunchDaemons/com.apple.syslogd.plist
</pre>

You need to edit this file to add a network listener. The plist is stored in a binary format so you need to use the plutil to convert it to XML using this command:

<pre>$ pushd /System/Library/LaunchDaemons
$ sudo plutil -convert xml1 /System/Library/LaunchDaemons/com.apple.syslogd.plist
$ sudo vim /System/Library/LaunchDaemons/com.apple.syslogd.plist
$ sudo plutil -convert binary1 /System/Library/LaunchDaemons/com.apple.syslogd.plist
$ sudo launchctl unload /System/Library/LaunchDaemons/com.apple.syslogd.plist
$ sudo launchctl load /System/Library/LaunchDaemons/com.apple.syslogd.plist
</pre>

Here is a complete example of the modified plist file. The new key is the NetworkListener. Be sure you add it nested inside the Sockets key or it will not work.

{% gist 1134216 %}

Once you have updated the plist the next step is to update the configuration of your AirPort Extreme. Under Applications => Utilities open the AirPort Utility and connect to your AirPort Extreme. On the Advanced tab select the “Logging & Statistics” panel. Enter the IP address of your Mac OS X Lion Server in “Syslog Destination Address:” and select “6 – Informational” for the “Syslog Level:”. You can see a screenshot of the AirPort Utility settings below. Update the settings on the AirPort Extreme.

<div>
  <img style="display:block; margin-left:auto; margin-right:auto;" src="http://www.idevelopsoftware.com/wp-content/uploads/2011/08/2011-08-09083214-AirPort-Utility-Focal-Shift-AirPort-Extreme.png" alt="AirPort Extreme Advanced Configuration" title="[2011-08-09083214]  AirPort Utility-Focal Shift AirPort Extreme.png" border="0" width="320" height="318" />
</div>

Now, you probably want to verify that the logging is actually happening. Open Console.app on your server and look at “All Messages”. While looking at the logs go to another machine (I used my MacBook Air with a wireless connection to the AirPort Extreme) and open System Preferences and then Network. Select your network adapter and ask for it to renew the DHCP lease. You should see some activity in the log.

Another way to verify the logging is to turn wifi off on your laptop. You should see a message like this:

<pre>8/9/11 8:43:09.000 AM 80211: Disassociated with station 60:33:4b:2c:de:c0
</pre>

When you turn wifi back on you will see something similar to this:

<pre>8/9/11 8:43:10.000 AM 80211: Rotated TKIP group key.
8/9/11 8:43:21.000 AM 80211: Associated with station 60:33:4b:2c:de:c0
8/9/11 8:43:21.000 AM 80211: Authenticating station 60:33:4b:2c:de:c0 to RADIUS.
8/9/11 8:43:21.000 AM 80211: Installed unicast CCMP key for supplicant 60:33:4b:2c:de:c0
8/9/11 8:43:21.000 AM natpmp: Binding added for udp, 173.164.164.17:32770 to 10.0.1.104:4500 with lifetime 7200
8/9/11 8:43:21.000 AM natpmp: Binding added for udp, 173.164.164.17:32771 to 10.0.1.104:5353 with lifetime 7200
</pre>

That’s it. You now have syslog data being captured on your Mac OS X Lion server from your AirPort Extreme base station!

