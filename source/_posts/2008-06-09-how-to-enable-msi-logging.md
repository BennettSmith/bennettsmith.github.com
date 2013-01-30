---
title: How to enable MSI Logging
author: bsmith
layout: post
permalink: /2008/06/how-to-enable-msi-logging/
categories:
  - Microsoft
  - Software
---
If you are trying to debug an installer problem it is probably worth having MSI logging turned on. This will produce a file in your %TEMP% directory that contains a detailed trace of the activities that took place in MSIEXEC. This can be very helpful when an install or uninstall fails without any clear indication as to why it failed. 

Log files are stored in the directory pointed to by the TEMP environment variable. The filename format is MSIxxxx.LOG, where xxxx is replaced with a random string. A new log file is created for each invocation of MSIEXEC. 

To enable logging through group policy, do the following:

*   Start / Run… / gpedit.msc
*   Drill down into `Local Computer Policy / Computer Configuration / Administrative Templates / Windows Components / Windows Installer / Logging`
*   Enable logging with the setting “voicewarmup”. These are the command-line arguments that MSIEXEC will use. 

These links contain more information on setting up logging:

*   [TechNet Article][1]
*   [PC Tools Guide][2]

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_29">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F06%2Fhow-to-enable-msi-logging%2F&linkname=How%20to%20enable%20MSI%20Logging" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F06%2Fhow-to-enable-msi-logging%2F&linkname=How%20to%20enable%20MSI%20Logging" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F06%2Fhow-to-enable-msi-logging%2F&linkname=How%20to%20enable%20MSI%20Logging" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>

 [1]: http://technet2.microsoft.com/windowsserver/en/library/0907105e-7856-4c93-b97f-a9a306623af51033.mspx?mfr=true
 [2]: http://www.pctools.com/guides/registry/detail/1127