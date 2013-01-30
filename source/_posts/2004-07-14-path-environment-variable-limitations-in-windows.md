---
title: PATH Environment Variable Limitations in Windows
author: Bennett Smith
layout: post
permalink: /2004/07/path-environment-variable-limitations-in-windows/
categories:
  - Microsoft
  - Software
---
Environment variables are managed using the System control panel applet in Windows. This user interface leaves much to be desired, but it works. Environment variables are separated into “System” and “User” categories. All users that may login on a machine share the System environment variables. Each user has her own set of User environment variables. User environment variables take precedence over System environment variables. How this precedence rule effects variable definitions is illustrated in the following example:

If the variable TEMP Generally speaking, if an environment variable appears in both categories then the value associated with the User environment variable will be used.

The PATH environment variable controls how the operating system searches for executable (EXE) and dynamic link library (DLL) files when asked to run an application. Some applications are installed for use by all users of the system and others are installed for exclusive use of a particular user.

Microsoft publishes some great human factors guidelines for building Windows applications. I sure wish they would follow some of these guidelines for the Control Panel applets that are provided with Windows. If these applets had to go through the logo certification process I’m sure they would fail!

Take for example the environment variable editing dialog box in the System applet.

[<img src="http://farm3.static.flickr.com/2018/2319758559_8f6f8596b9_o.jpg" alt="EnvironmentVariables-thumb" border="0" width="250" height="231" />][1]

This is a prefect example of what not to do when building a user interface. I hate editing environment variables using a one line edit box where you can’t even see the whole definition of the value. You can’t even resize the dialog box!

To make matters worse, there are limits imposed by the operating system that are not checked in the user interface. The PATH environment variable cannot exceed 1024 characters in length, but the user interface happily allows you to define a PATH that is way longer than this.

You can try this for yourself by defining a System PATH that is about 512 bytes in length and define a User PATH that is about 600 bytes long. Because the combine System+User PATH is longer than 1024 bytes the operating system decides to only use the System PATH, leaving out all your User PATH assignments.

A good user environment variable editor would check for this sort of thing. Since Microsoft doesn’t need to get their applications “logo certified” they can freely ignore the UI guidelines they publish. What a shame!

I looked into what it would take to create my own Control Panel Applet to replace this environment variable editor and it looks straight forward. Keep tuned, and maybe I’ll post an improved editor here.

As I dig further into this environment variable issue it seems like there is a lot of inconsistency between versions of Windows.

Microsoft has some [information][2] on the NT command prompt for Windows XP that says the maximum environment variable size is 8192 bytes and that the entire environment cannot exceed 65,536KB (though I think that is supposed to be bytes).

Early versions of MS-DOS had a 128 character limitation on the PATH variable. According to this [article][3], that limitation was removed in MS-DOS 6.0. In [KB169171][4] Microsoft talks about how 16-bit applications can still hang when the path exceeds 200 bytes.

The only place I could find that actually states that there is a 1KB limit on the combine length of the System+User path is [here][5]. In the WORKAROUND section of this article it states that the path should “total 1 KB or less of characters”. The article is for Windows NT Server 4.0 Terminal Server Edition, but my experiments on a Windows 2000 Professional system indicate that it is still the case. I haven’t tried Windows XP or Windows Server 2003 yet to determine if the problem exists in those variants of Windows.

 [1]: http://www.flickr.com/photos/49807087@N00/2319758559 "View 'EnvironmentVariables-thumb' on Flickr.com"
 [2]: http://technet.microsoft.com/en-us/library/bb490998.aspx
 [3]: http://support.microsoft.com/default.aspx?scid=kb;en-us;97595
 [4]: http://support.microsoft.com/default.aspx?scid=kb;EN-US;169171
 [5]: http://support.microsoft.com/default.aspx?scid=kb;en-us;216477
