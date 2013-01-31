---
title: Simple UI Refinements Increase Developer Productivity
author: Bennett Smith
layout: post
date: 2008-06-27 08:00
permalink: /2008/06/simple-ui-refinements-increase-developer-productivity/
categories:
  - Software
---
Recently I have been thinking a lot about what it takes to create a good user interface versus one that just gets the job done. Whole books are available about UI design, but I think most developers steer clear of them, adopting a [*Git-R-Done*][1] attitude instead.

Most developers that do UI work know how to use the various widgets, can follow the general patterns that can be observed in other platform applications (i.e. copy the UI “feel”), and have a vague sense of how to lay out the elements of a dialog box. What we all seem to forget is that the field of human interaction is separate from programming, and that there really is something to it.

A very good example of how subtle changes in a UI can make all the difference can be found in Visual Studio and Xcode; the development environments for Windows and Mac OS X. In both tools a dialog is provided for manipulating the compiler and linker settings that control how the project is build.

Visual Studio 2005 – nice set of property pages that can be navigated by a tree on the left. The problem is, you have to already know where all the properties live (under which tab) in order to quickly navigate to the properties you want to change. Take a look at the screenshot to see what I’m talking about.

[<img src="http://idvlpsw.files.wordpress.com/2008/06/vc2005-properties-thumb.png" alt="vc2005_properties_thumb.png" border="0" width="320" height="211" align="left" />][2]

Apple took a similar but subtly different approach on their project properties dialog box. They list all properties by default, grouping them by category. The developer can scroll up/down through the complete list to browse all of the properties. The search box at the top of the dialog provides a more powerful user interface than the tree control in Visual Studio. This one little addition makes all the difference in the world for a busy developer.

[<img src="http://idvlpsw.files.wordpress.com/2008/06/xcode-project-properties-thumb.png" alt="Xcode Project Properties_thumb.png" border="0" width="320" height="245" align="left" />][3]

Here we see how this simple addition can increase the productivity of a developer. By simply letting the developer type a free-form string that describes part of the property he/she wishes to change the list of properties is narrowed to display only those that are a match. In the screenshot below you can see how this makes it very easy to get at the preprocessor definitions to make a quick change. In Visual Studio the developer is expected to remember which category the property appears in, remember the name of the category, and then navigate to that tab before he/she can make the change.

[<img src="http://idvlpsw.files.wordpress.com/2008/06/xcode-project-properties-narrowed-thumb.png" alt="Xcode Project Properties (Narrowed)_thumb.png" border="0" width="320" height="245" align="left" />][4]

This is just one small example of how similar user interfaces can be very different when actually used. Both provide a way to manage the properties of a project, but only Xcode provides solid UI features that support the day-to-day use cases for a busy developer.

So, it should be clear that spending time on UI design can pay off. Your users may not recognize the amount of effort that was put into the UI, but they will appreciate the increased productivity that a well though out UI provides.


 [1]: http://en.wikipedia.org/wiki/Larry_the_Cable_Guy
 [2]: http://idvlpsw.files.wordpress.com/2008/06/vc2005_properties.png
 [3]: http://idvlpsw.files.wordpress.com/2008/06/xcode-project-properties.png
 [4]: http://idvlpsw.files.wordpress.com/2008/06/xcode-project-properties-narrowed.png
