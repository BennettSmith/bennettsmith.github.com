---
title: 'HOWTO &#8211; Use Visual Studio 2005 for Qt Open Source Development'
author: Bennett Smith
layout: post
permalink: /2006/02/howto-use-visual-studio-2005-for-qt-open-source-development/
categories:
  - How To
  - Microsoft
  - Qt
---
*THIS IS A WORK IN PROGRESS. EXPECT UPDATES AND DON’T BE SURPRISED BY INCOMPLETE INFORMATION*<span class="alignright"><a target="_blank" href="http://www.trolltech.com"><img src="http://idvlpsw.files.wordpress.com/2008/03/qt.png" alt="qtlogo_feature.png" border="0" /></a></span>

Trolltech has released Qt 4 under a dual-license for all supported platforms. In earlier versions of Qt they only released the open source version for Mac and Linux, leaving Windows developers with no choice but to purchase a commercial license. That all changed with the release of Qt 4 when Trolltech started to provide an open source version for Windows development too! The only catch was that Trolltech only supports the MinGW GCC compiler for development using the open source version.

This article describes how to patch Qt 4 open source edition on Windows so you can develop using Visual Studio 2005. You can even develop using the free Express edition of Visual Studio 2005 so long as you also install the latest Platform SDK.

Please keep in mind that these patches and tips are not provided so you can get around the very generous Trolltech dual-license terms of use. If you are developing or intend to develop a commercial application using Qt 4 you must purchase a commercial license for Qt 4. Only use the information provided in this article if you wish to develop open source GPL software for the Windows platform and wish to use the Microsoft Visual C++ 2005 compiler instead of the MinGW GCC compiler.

## Download Qt 4.1 Source Code, Patches, and Notes

*   Download the latest open source Windows version of Qt 4.1 from Trolltech at http://www.trolltech.com/download/qt/windows.html. Unzip the file to C:\. It will extract all of the files into a sub-directory called qt-win-opensource-src-4.1.0.
*   Download the latest patch file used to modify the open source version of Qt 4.1 to support Microsoft Visual Studio 2005 from Source Forge at http://sourceforge.net/projects/qtwin/. Unzip the file to C:\qt-win-opensource-src-4.1.0.
*   Download the build script, environment setup and notes from http://www.idevelopsoftware.com/downloads/qt/Qt41WinBuildScript.zip. Unzip the file to C:\qt-win-opensource-src-4.1.0.
*   If you don’t already have Visual Studio 2005 you can download the Express edition. You will also need to download the Platform SDK. 
    http://msdn.microsoft.com/vstudio/express/visualC/default.aspx
    
    http://msdn.microsoft.com/vstudio/express/visualc/usingpsdk/default.aspx

## Building Qt 4.1 using Visual C++ 2005

Open C:\qt-win-opensource-src-4.1.0 in Windows Explorer.  
Double-click on the “Qt 4.1 Command Prompt” shortcut to open a Command Prompt window with the environment setup for Qt 4.1 development. IMPORTANT: You must already have Visual Studio 2005 installed. You may need to edit setenv.cmd if your copy of Visual Studio 2005 is not in the default location.

Run “installpatch41.bat”  
This will patch the Qt 4.1 source code so it builds properly using the Visual C++ 2005 compiler.

Run “build.cmd”  
This will build all of the Qt 4.1 libraries, utilities, and sample applications using the Visual C++ 2005 compiler.

To rebuild, if necessary, make sure to first clean up the previous build. Do this by running  
nmake distclean

from the C:\qt-win-opensource-src-4.1.0 directory.

External Tools Configuration in Visual Studio 2005

Launch Visual Studio 2005 and select the “External Tools…” item from the Tools menu.  
Use the “Add button to define each of the following external tools:

Title ……………….. QMake (Project File Generation Mode)  
Command ……………… D:\qt-win-opensource-src-4.1.0\bin\qmake.exe  
Arguments ……………. -project -spec win32-msvc2005  
Initial directory …….. $(ProjectDir)  
Use Output window …….. [X]  
Treat output as Unicode .. [ ]  
Prompt for arguments ….. [ ]  
Close on exit ………… [X]

Title ……………….. QMake (Makefile Generation Mode)  
Command ……………… D:\qt-win-opensource-src-4.1.0\bin\qmake.exe  
Arguments ……………. -makefile -spec win32-msvc2005  
Initial directory …….. $(ProjectDir)  
Use Output window …….. [X]  
Treat output as Unicode .. [ ]  
Prompt for arguments ….. [ ]  
Close on exit ………… [X]

Title ……………….. Qt Designer  
Command ……………… D:\qt-win-opensource-src-4.1.0\bin\designer.exe  
Arguments …………….  
Initial directory …….. $(ProjectDir)  
Use Output window …….. [ ]  
Treat output as Unicode .. [ ]  
Prompt for arguments ….. [ ]  
Close on exit ………… [ ]

Title ……………….. Qt Assistant  
Command ……………… D:\qt-win-opensource-src-4.1.0\bin\assistant.exe  
Arguments …………….  
Initial directory …….. $(ProjectDir)  
Use Output window …….. [ ]  
Treat output as Unicode .. [ ]  
Prompt for arguments ….. [ ]  
Close on exit ………… [ ]  
Adding a Qt 4.1 Development Toolbar

Add a new toolbar for Qt 4.1 Development by selecting “Customize…” from the Tools menu. Once the “Customize” dialog appears select the “Toolbars” tab and press “New…” For the toolbar name enter “Qt 4.1 Development” and press “OK”.  
Select the “Commands” tab on the “Customize” dialog. Select “Tools” from the “Categories:” list. Scroll down in the “Commands:” list until you see “External Command 7″. Drag commands 7, 8, 9, and 10 onto the new “Qt 4.1 Development” toolbar.  
Creating a New Visual Studio 2005 Project

Open the “New Project” dialog by selecting File->New->Project… from the menu. Under “Project types” on the left side of the dialog expand “Visual C++” and then select “General.” The right side of the dialog will display a list of all the general project types. Select “Makefile Project” from the list of project types. Provide a name for the project and set the location on disk where you wish the project to be saved. Be sure not to check “Create directory for solution”, as this will create an extra level of directories that is just confusing. Click the “OK” button and you will be presented with the “Makefile Application Wizard.” Simply press the “Finish” button on the first page of the wizard.

Once the project has been created and opened, set the NMake Configuration Properties for the project as shown below. In the “Solution Explorer” right-click on the name of your project. Select “Properties…” from the context menu. On the property pages dialog select “Configuration Properties” and “NMake” on the left side tree control. On the right side, enter the following information, making sure to set the properties for both the debug and release configurations.

Release Configuration Settings

General  
——-  
Build Command Line …………………. nmake release-all  
Rebuild All Commaond Line …………… nmake release-clean release-all  
Clean Command Line …………………. nmake release-clean  
Output ……………………………. foo.exe

IntelliSense  
————  
Common Language Runtime Support ……… No Common Language Runtime support  
Preprocessor Definitions ……………. WIN32;NDEBUG;UNICODE;QT\_LARGEFILE\_SUPPORT;QT_DLL;  
QT\_GUI\_LIB;QT\_CORE\_LIB;QT\_THREAD\_SUPPORT  
Include Search Path ………………… “c:/qt-win-opensource-src-4.1.0/include/QtCore”;  
“c:/qt-win-opensource-src-4.1.0/include/QtGui”;  
“c:/qt-win-opensource-src-4.1.0/include”;  
“c:/qt-win-opensource-src-4.1.0/include/ActiveQt”;  
“c:/qt-win-opensource-src-4.1.0/mkspecs/win32-msvc2005″  
Forced Includes …………………….  
Assembly Search Path ………………..  
Forced Using Assemblies ……………..  
Debug Configuration Settings

General  
——-  
Build Command Line …………………. nmake debug-all  
Rebuild All Commaond Line …………… nmake debug-clean debug-all  
Clean Command Line …………………. nmake debug-clean  
Output ……………………………. food.exe

IntelliSense  
————  
Common Language Runtime Support ……… No Common Language Runtime support  
Preprocessor Definitions ……………. WIN32;\_DEBUG;UNICODE;QT\_LARGEFILE\_SUPPORT;QT\_DLL;  
QT\_GUI\_LIB;QT\_CORE\_LIB;QT\_THREAD\_SUPPORT  
Include Search Path ………………… “c:/qt-win-opensource-src-4.1.0/include/QtCore”;  
“c:/qt-win-opensource-src-4.1.0/include/QtGui”;  
“c:/qt-win-opensource-src-4.1.0/include”;  
“c:/qt-win-opensource-src-4.1.0/include/ActiveQt”;  
“c:/qt-win-opensource-src-4.1.0/mkspecs/win32-msvc2005″  
Forced Includes …………………….  
Assembly Search Path ………………..  
Forced Using Assemblies ……………..  
QMake Project Settings

Create a project file called “foo.pro” in the directory for your makefile project. Replace the name “foo.pro” with the name of your actual application. Place the file in the directory where your Visual Studio project was created. To start with, the contents might look something like this:

CONFIG += qt  
TEMPLATE = app  
SOURCES += foo.cpp  
HEADERS += foo.h  
FORMS += foo.ui  
You should be off and running now. For more detailed information I would suggest reading the qmake reference manual. You might also want to take a look at the Qt 4.1 tutorials in Qt Assistant. Have fun!

