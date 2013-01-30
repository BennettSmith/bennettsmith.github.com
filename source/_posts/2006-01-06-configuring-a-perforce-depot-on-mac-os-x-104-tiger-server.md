---
title: Configuring a Perforce Depot on Mac OS X 10.4 (Tiger) Server
author: bsmith
layout: post
permalink: /2006/01/configuring-a-perforce-depot-on-mac-os-x-104-tiger-server/
categories:
  - SCM Tools
  - Software
---
Download the latest version of Perforce from their web site (http://www.perforce.com). To setup the server you really only need to download the command-line tools p4 and p4d. Here are links to the versions I used when setting up my server in January 2006.

http://www.perforce.com/downloads/perforce/r05.2/bin.macosx102ppc/p4

http://www.perforce.com/downloads/perforce/r05.2/bin.darwin60ppc/p4d

You may also wish to install the graphical tools P4V and P4Merge. These are part of a single disk image.

http://www.perforce.com/downloads/perforce/r05.2/bin.macosx102ppc/P4V.dmg

Perforce recommends that p4d not be run as root so I created a new user account called p4admin. I also created a new group called perforce. I decided to install the software in the /usr/local/bin directory and to place the depot on a separate drive that is mounted under the /Depot directory.

Automatically starting p4d when the system boots is handled through the utility launchd. Configuring this is done by editing a plist file and then loading it with the utility launchctl. Attached is a copy of the plist file I used. I placed the plist file in the directory /Library/LaunchDaemons. The file is called perforce.plist.

Once the file exists use the launchctl application to tell the launchd program about it. The command I used was:

$ sudo launchctl load /Library/LaunchDaemons/perforce.plist

If you make changes to the plist file and want to reload it use the command below to unload the existing one. Then repeat the above command to load the changed plist.

$ sudo launchctl unload /Library/LaunchDaemons/perforce.plist

Perforce recommends setting up a regular job to create a checkpoint and a backup of the depot. The script p4backup illustrates how to handle this. Use the p4backup.plist file to teach launchd about this script so it will run on a regular basis. On my server I run this script every night. The backup is done using a copy from the /Depot directory to the /Depot.Backup directory, which is on a separate filesystem.

perforce.plist GroupName perforce Label com.perforce.p4d OnDemand Program /usr/local/bin/p4d ProgramArguments /usr/local/bin/p4d -r /Depot -p 1666 -J /Depot/journal -L /Depot/p4err RunAtLoad ServiceDescription Perforce Daemon StandardErrorPath /Depot/p4d.stderr.txt StandardOutPath /Depot/p4d.stdout.txt UserName p4admin WorkingDirectory /Depot

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_11">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2006%2F01%2Fconfiguring-a-perforce-depot-on-mac-os-x-104-tiger-server%2F&linkname=Configuring%20a%20Perforce%20Depot%20on%20Mac%20OS%20X%2010.4%20%28Tiger%29%20Server" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2006%2F01%2Fconfiguring-a-perforce-depot-on-mac-os-x-104-tiger-server%2F&linkname=Configuring%20a%20Perforce%20Depot%20on%20Mac%20OS%20X%2010.4%20%28Tiger%29%20Server" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2006%2F01%2Fconfiguring-a-perforce-depot-on-mac-os-x-104-tiger-server%2F&linkname=Configuring%20a%20Perforce%20Depot%20on%20Mac%20OS%20X%2010.4%20%28Tiger%29%20Server" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>