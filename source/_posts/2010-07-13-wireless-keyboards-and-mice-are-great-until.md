---
title: 'Wireless Keyboards and Mice are Great Until&#8230;.'
author: Admin
layout: post
permalink: /2010/07/wireless-keyboards-and-mice-are-great-until/
categories:
  - Apple
  - Blog
  - Hardware
---
Tonight I sat down at my 27″ iMac to get a little work done. The first thing I do is tap the keyboard and move the mouse to wake the machine from sleep mode. The machine awoke and then quickly displayed the *Connection Lost* graphics in the middle of the screen for both the mouse and keyboard. My first thought; no problem, it’s just the batteries so I replaced them. Still no connection (and it did seem kind of odd for both the mouse and keyboard batteries to be dead at the same time.) Looking up at the system tray I see an odd Bluetooth icon. Here’s a closeup of what I found: 

<div style="text-align:center;">
  <img src="http://www.idevelopsoftware.com/wp-content/uploads/2010/07/LittleSnapper.png" alt="LittleSnapper.png" border="0" width="280" height="69" align="center" />
</div>

The *Bluetooth: Not Available* message in the system tray is not a good sign. Next I opened up *Console.app* to see if there were any indications of what the root cause for this behavior was. It appears there is truly something wrong with the Bluetooth Module. Here is what it showed: 

<div style="text-align:center;">
  <img src="http://www.idevelopsoftware.com/wp-content/uploads/2010/07/Console2.png" alt="[AppleUSBBluetoothHCIController][FindInterfaces] some interface pipes were not found. Device is no good a a transport" border="0" width="730" height="124" align="center" />
</div>

A visit to the support forums at Apple led me to an idea to reset the SMC on the iMac. I tried that and still nothing. At this point I’m not a happy camper. It is looking like the Bluetooth Module in my iMac has given up the ghost. 

Next step, the iPhone Apple AppStore application to make a Genius Bar appointment. 

<div style="text-align:center;">
  <img src="http://www.idevelopsoftware.com/wp-content/uploads/2010/07/genius.png" alt="genius.png" border="0" width="213" height="320" align="center" />
</div>

If you have read this far then you might be wondering why I’m telling you all of this. The reason is simple. Without a USB keyboard and mouse laying around somewhere none of the troubleshooting above would have been possible. Having a wireless bluetooth keyboard and mouse ship by default with the iMac is a really odd choice on Apple’s part. 

Thankfully I have a keyboard and mouse from the Xserve in my garage. In case you forgot what these old fashion beasts look like, here’s a picture of the dynamic duo that saved my bacon tonight! 

<div style="txt-align:center;">
  <img src="http://www.idevelopsoftware.com/wp-content/uploads/2010/07/backup_plan.png" alt="backup_plan.png" border="0" width="640" height="478" align="center" />
</div>

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_59">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2010%2F07%2Fwireless-keyboards-and-mice-are-great-until%2F&linkname=Wireless%20Keyboards%20and%20Mice%20are%20Great%20Until%26%238230%3B." title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2010%2F07%2Fwireless-keyboards-and-mice-are-great-until%2F&linkname=Wireless%20Keyboards%20and%20Mice%20are%20Great%20Until%26%238230%3B." title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2010%2F07%2Fwireless-keyboards-and-mice-are-great-until%2F&linkname=Wireless%20Keyboards%20and%20Mice%20are%20Great%20Until%26%238230%3B." title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>