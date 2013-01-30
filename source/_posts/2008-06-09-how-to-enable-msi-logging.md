---
title: How to enable MSI Logging
author: Bennett Smith
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


 [1]: http://technet2.microsoft.com/windowsserver/en/library/0907105e-7856-4c93-b97f-a9a306623af51033.mspx?mfr=true
 [2]: http://www.pctools.com/guides/registry/detail/1127
