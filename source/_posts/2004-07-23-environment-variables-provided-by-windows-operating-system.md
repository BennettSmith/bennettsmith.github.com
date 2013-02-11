---
title: Environment Variables Provided by Windows Operating System
author: Bennett Smith
layout: post
date: 2004-07-23 08:00
permalink: /2004/07/environment-variables-provided-by-windows-operating-system/
categories:
  - Microsoft
  - Software
---
Microsoft assigns a type to each environment variable that is part of the environment block of a process. The possible types are System, User, Volatile and Process.

System
:   An environment variable that contains the same value for all processes running on the system, regardless of which user the process runs as. These are shared or global environment variables, and are defined in the system registry under the HKEY\_LOCAL\_MACHINE hive.

User
:   An environment variable that is specified for a particular user on the system. These are defined in the system registry as well, but are maintained under the HKEY\_CURRENT\_USER hive.

Volatile
:   An environment variable that is not persistent, and has a value that was assigned by the operating system based on some property of the system.

Process
:   An environment variable that is set only for a particular process. Often this would be set in the environment block by the parent process at the time the process is created. These are not persistent.

Additionally, the CMD.EXE command processor defines some dynamic environment variables that are assigned new values after each command is evaluated. These variables are volatile.

These tables were created by going through the on-line help for Windows 2000. I have listed all the volatile and dynamic environment variables I could find defined. There are probably more, and some of these may not be accurately documented.

<table>
  <tr>
    <th colspan="2" align="center">
      Volatile Environment Variables
    </th>
  </tr>
  
  <tr>
    <th>
      Name
    </th>
    
    <th>
      Description
    </th>
  </tr>
  
  <tr>
    <td>
      ALLUSERSPROFILE
    </td>
    
    <td>
      Local – returns the location of the All Users Profile.
    </td>
  </tr>
  
  <tr>
    <td>
      APPDATA
    </td>
    
    <td>
      Local – returns the location where applications store data by default.
    </td>
  </tr>
  
  <tr>
    <td>
      COMPUTERNAME
    </td>
    
    <td>
      System – returns the name of the computer.
    </td>
  </tr>
  
  <tr>
    <td>
      HOMESHARE
    </td>
    
    <td>
      System – returns the network path to the user’s shared home directory. This variable is set based on the value of the home directory. The user’s home directory is specified in Local Users and Groups.
    </td>
  </tr>
  
  <tr>
    <td>
      LOGONSERVER
    </td>
    
    <td>
      Local – returns the name of the domain controller that validated the current logon session.
    </td>
  </tr>
  
  <tr>
    <td>
      USERDOMAIN
    </td>
    
    <td>
      Local – returns the name of the domain that contains the user’s account.
    </td>
  </tr>
  
  <tr>
    <td>
      USERNAME
    </td>
    
    <td>
      Local – returns the name of the user currently logged on.
    </td>
  </tr>
  
  <tr>
    <td>
      USERPROFILE
    </td>
    
    <td>
      Local – returns the location of the profile for the current user.
    </td>
  </tr>
  
  <tr>
    <td>
      NUMBER_OF_PROCESSORS
    </td>
    
    <td>
      Number of processors running on the machine.
    </td>
  </tr>
  
  <tr>
    <td>
      PROCESSOR_ARCHITECTURE
    </td>
    
    <td>
      Processor type of the user’s workstation.
    </td>
  </tr>
  
  <tr>
    <td>
      PROCESSOR_IDENTIFIER
    </td>
    
    <td>
      Processor ID of the user’s workstation.
    </td>
  </tr>
  
  <tr>
    <td>
      PROCESSOR_LEVE
    </td>
    
    <td>
      Processor level of the user’s workstation.
    </td>
  </tr>
  
  <tr>
    <td>
      PROCESSOR_REVISION
    </td>
    
    <td>
      Processor version of the user’s workstation.
    </td>
  </tr>
  
  <tr>
    <td>
      OS
    </td>
    
    <td>
      Operating system on the user’s workstation.
    </td>
  </tr>
  
  <tr>
    <td>
      COMSPEC
    </td>
    
    <td>
      Executable file for the command prompt (typically cmd.exe).
    </td>
  </tr>
  
  <tr>
    <td>
      HOMEDRIVE
    </td>
    
    <td>
      Primary local drive (typically the C drive).
    </td>
  </tr>
  
  <tr>
    <td>
      HOMEPATH
    </td>
    
    <td>
      Default directory for users (typically \users\default in Windows 2000).
    </td>
  </tr>
  
  <tr>
    <td>
      PATH
    </td>
    
    <td>
      PATH environment variable.
    </td>
  </tr>
  
  <tr>
    <td>
      PATHEXT
    </td>
    
    <td>
      Extensions for executable files (typically .com, .exe, .bat, or .cmd).
    </td>
  </tr>
  
  <tr>
    <td>
      PROMPT
    </td>
    
    <td>
      Command prompt (typically $P$G).
    </td>
  </tr>
  
  <tr>
    <td>
      SYSTEMDRIVE
    </td>
    
    <td>
      Local drive on which the system directory resides (typcially c:\).
    </td>
  </tr>
  
  <tr>
    <td>
      SYSTEMROOT
    </td>
    
    <td>
      System directory (for example, c:\winnt). This is the same as WINDIR.
    </td>
  </tr>
  
  <tr>
    <td>
      WINDIR
    </td>
    
    <td>
      System directory (for example, c:\winnt). This is the same as SYSTEMROOT.
    </td>
  </tr>
  
  <tr>
    <td>
      TEMP
    </td>
    
    <td>
      Directory for storing temporary files (for example, c:\temp).
    </td>
  </tr>
  
  <tr>
    <td>
      TMP
    </td>
    
    <td>
      Directory for storing temporary files (for example, c:\temp).
    </td>
  </tr>
</table>

<table>
  <tr>
    <th colspan="2" align="center">
      Dynamic Environment Variables
    </th>
  </tr>
  
  <tr>
    <th>
      Name
    </th>
    
    <th>
      Description
    </th>
  </tr>
  
  <tr>
    <td>
      CD
    </td>
    
    <td>
      Expands to the current directory.
    </td>
  </tr>
  
  <tr>
    <td>
      DATE
    </td>
    
    <td>
      Expands to the same output as typing DATE.
    </td>
  </tr>
  
  <tr>
    <td>
      TIME
    </td>
    
    <td>
      Expands to the same output as typing TIME.
    </td>
  </tr>
  
  <tr>
    <td>
      RANDOM
    </td>
    
    <td>
      Generates a random integer in the range of 0 – 32767.
    </td>
  </tr>
  
  <tr>
    <td>
      ERRORLEVEL
    </td>
    
    <td>
      Expands to the current ERRORLEVEL.
    </td>
  </tr>
  
  <tr>
    <td>
      CMDEXTVERSION</td <td>
        Expands to the current Command Processor Extensions version number.
      </td></tr> 
      
      <tr>
        <td>
          CMDCMDLINE
        </td>
        
        <td>
          Expands to the original command line that invoked the Command Processor.
        </td>
      </tr></table> 
