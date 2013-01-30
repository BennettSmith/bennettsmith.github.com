---
title: Working with Multiple Depots and/or Client Workspaces
author: Bennett Smith
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

