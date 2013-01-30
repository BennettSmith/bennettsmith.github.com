---
title: Generating a GDB Log File for Xcode Debug Sessions
author: bsmith
layout: post
permalink: /2008/02/generating-a-gdb-log-file-for-xcode-debug-sessions/
categories:
  - Apple
  - Objective-C
  - Software
  - Xcode
---
If you would like to capture a log of everything that GDB displays during a debugging session you can do the following:  
`<br />
$ defaults write com.apple.Xcode PBXGDBDebuggerLogToFile YES<br />
`  
The statement above will turn on logging to a file. Now, you need to set the filename for the debugger output file. Use the following statement to accomplish that.  
`<br />
$ defaults write com.apple.Xcode PBXGDBDebuggerLogFileName /tmp/gdboutput.log<br />
`  
This will create a file in the /tmp directory called gdboutput.log, containing everything you see in the GDB command window during your debugging session.

Both of these commands need to be typed into a Terminal.app window. You only need to do this once, as your machine will remember the settings.

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_15">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F02%2Fgenerating-a-gdb-log-file-for-xcode-debug-sessions%2F&linkname=Generating%20a%20GDB%20Log%20File%20for%20Xcode%20Debug%20Sessions" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F02%2Fgenerating-a-gdb-log-file-for-xcode-debug-sessions%2F&linkname=Generating%20a%20GDB%20Log%20File%20for%20Xcode%20Debug%20Sessions" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F02%2Fgenerating-a-gdb-log-file-for-xcode-debug-sessions%2F&linkname=Generating%20a%20GDB%20Log%20File%20for%20Xcode%20Debug%20Sessions" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>