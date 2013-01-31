---
title: Generating a GDB Log File for Xcode Debug Sessions
author: Bennett Smith
layout: post
date: 2008-02-02 08:00
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

