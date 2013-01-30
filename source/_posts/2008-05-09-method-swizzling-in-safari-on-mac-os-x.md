---
title: Method Swizzling in Safari on Mac OS X
author: Bennett Smith
layout: post
permalink: /2008/05/method-swizzling-in-safari-on-mac-os-x/
categories:
  - Apple
  - Objective-C
  - Xcode
tags:
  - How To
---
Recently I have been working on an extension for the Safari web browser. The biggest challenge when developing an extension for Safari is determining how to hook your code into Safari.app. Most browsers these days provide hooks to allow development of extensions, but Safari does not.

A technique that many people use to add functionality to Safari (and other Cocoa applications) is called Method Swizzling. If you want to learn more about this technique there is a [terrific article][1] explaining all the details on the CocoaDev site.

When applying the method swizzling technique you may find that the linker complains about *unresolved classes* and won’t link your bundle. This issue usually crops up when you try swizzling a method that is in a class you learned about by running [class-dump][2] or by using [FScript][3]. If you run into this problem bring up the project properties in Xcode and add `-undefined dynamic_lookup` to the **Other Linker Flags** section.

Without this extra flag your plug-in will not link, and you will be stuck in the mud! Thanks to Aaron Harnly, author of [Letterbox][4], for pointing this out to me in an e-mail exchange.


 [1]: http://www.cocoadev.com/index.pl?MethodSwizzling
 [2]: http://www.codethecode.com/projects/class-dump/
 [3]: http://www.fscript.org
 [4]: http://harnly.net/software/letterbox
