---
title: Working with Multiple Depots and/or Client Workspaces
author: bsmith
layout: post
permalink: /2006/01/working-with-multiple-depots-andor-client-workspaces/
categories:
  - SCM Tools
  - Software
---
A typical configuration of Perforce is handled by setting the P4PORT, P4USER and P4CLIENT environment variables. These variables point at the desired depot, identify the user and select a client workspace.

To quickly switch between different depots or client workspaces I make sure the P4CONFIG environment variable specifies the name of a configuration file. On my Windows XP system this is done by running the command p4 set P4CONFIG=p4config.txt. The p4 command will recognize that this variable is set and will attempt to locate a configuration file each time it is launched. The search begins in the current directory and searches all parent directories until it reaches the root directory for the current drive.

I place a p4config.txt file in each workspace root directory. The file is formatted as a series of lines where each line contains name=value. For example, one of my p4config.txt files looks like this:

P4CLIENT=bsmith_pc  
P4EDITOR=C:\Program Files\Vim\vim63\vim.exe  
P4PORT=perforce.mysite.com:1666  
P4USER=bsmith

My installation of Perforce is configured to use the ticket-based authentication system so I can login to the depot by issuing the p4 login command from a directory below the workspace root. I will be prompted for the password and a ticket will be issued. From this point on I can simply issue p4 commands and the appropriate depot and workspace will be automatically selected.

This technique can be applied to multiple client workspaces at the same time by setting up multiple p4config.txt files and logging into each depot. Then it is a simple matter of changing directories in my command window to switch between depots and/or client workspaces.

On Unix and Mac OS X I set P4CONFIG to point at a file called @.p4config@. The file contents are similar to the Windows example earlier in this post.

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_12">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2006%2F01%2Fworking-with-multiple-depots-andor-client-workspaces%2F&linkname=Working%20with%20Multiple%20Depots%20and%2For%20Client%20Workspaces" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2006%2F01%2Fworking-with-multiple-depots-andor-client-workspaces%2F&linkname=Working%20with%20Multiple%20Depots%20and%2For%20Client%20Workspaces" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2006%2F01%2Fworking-with-multiple-depots-andor-client-workspaces%2F&linkname=Working%20with%20Multiple%20Depots%20and%2For%20Client%20Workspaces" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>