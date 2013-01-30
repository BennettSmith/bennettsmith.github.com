---
title: Backup MySQL database on Windows Server 2003
author: bsmith
layout: post
permalink: /2004/12/backup-mysql-database-on-windows-server-2003/
categories:
  - Software
---
ere are a couple scripts that I use to automatically backup a MySQL database on a Windows 2003 Server system.

The first script is called getdatetime.cmd. It is a reusable script to get the current date/time in some environment variables.

<pre>@echo off

rem *******************************************************************
rem
rem Set environment variables with date/time information.
rem
rem DT_MONTH .................... Two digit month
rem DT_DAY ...................... Two digit day
rem DT_YEAR ..................... Four digit year
rem DT_HOUR ..................... Two digit hour
rem DT_MINUTE ................... Two digit minute
rem DT_SECOND ................... Two digit second
rem DT_RFC ...................... YYYYMMDDTHHMMSS
rem
rem *******************************************************************

rem Grab date and time values for conversion.

SET _CUR_DATE=%DATE%
SET _CUR_TIME=%TIME%

rem Convert from "Mon 10/27/2003" to individual parts by using a DOS FOR loop.

FOR /F "tokens=1-4 delims=/.- " %%a IN ("%_CUR_DATE%") DO SET DT_MONTH=%%b
FOR /F "tokens=1-4 delims=/.- " %%a IN ("%_CUR_DATE%") DO SET DT_DAY=%%c
FOR /F "tokens=1-4 delims=/.- " %%a IN ("%_CUR_DATE%") DO SET DT_YEAR=%%d

rem Convert from "11:40:12.82" to individual parts by using a DOS FOR loop.

FOR /F "tokens=1-4 delims=:." %%a IN ("%_CUR_TIME%") DO SET DT_HOUR=%%a
FOR /F "tokens=1-4 delims=:." %%a IN ("%_CUR_TIME%") DO SET DT_MINUTE=%%b
FOR /F "tokens=1-4 delims=:." %%a IN ("%_CUR_TIME%") DO SET DT_SECOND=%%c

SET DT_RFC=%YEAR%%MONTH%%DAY%T%HOUR%%MINUTE%%SECOND%
</pre>

The second script does the actual work of backing up the database. It references the getdatetime.cmd script. Make sure you save both scripts in the same directory. I call this script nightly-backup.cmd, but you can call it anything you wish.

<pre>@echo off
rem
rem Perform a backup of the MySQL database called mtblog.  This
rem is the database with the Movabletype web log data in it.
rem

rem Get date/time values
call GetDateTime.cmd
SET YEAR=%DT_YEAR%
SET MONTH=%DT_MONTH%
SET DAY=%DT_DAY%
SET HOUR=%DT_HOUR%
SET MINUTE=%DT_MINUTE%
SET SECOND=%DT_SECOND%

rem Figure out what the filename should be for this backup.
SET BACKUP_FILE=C:\MT-3.11-full-en_us\db-backups\mtblog-backup-%YEAR%%MONTH%%DAY%T%HOUR%%MINUTE%%SECOND%.sql

rem Perform the backup.
c:\mysql\bin\mysqldump --host=localhost --password=password --user=root mtblog &gt; %BACKUP_FILE%
</pre>

Don’t forget to change the host, password, and user information on the last line of the script. You may also need to change the path to the mysqldump program if it is not under c:\mysql\bin on your system.

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_9">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2004%2F12%2Fbackup-mysql-database-on-windows-server-2003%2F&linkname=Backup%20MySQL%20database%20on%20Windows%20Server%202003" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2004%2F12%2Fbackup-mysql-database-on-windows-server-2003%2F&linkname=Backup%20MySQL%20database%20on%20Windows%20Server%202003" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2004%2F12%2Fbackup-mysql-database-on-windows-server-2003%2F&linkname=Backup%20MySQL%20database%20on%20Windows%20Server%202003" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>