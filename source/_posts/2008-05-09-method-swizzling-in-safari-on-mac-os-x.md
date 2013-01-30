---
title: Method Swizzling in Safari on Mac OS X
author: bsmith
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

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_26">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F05%2Fmethod-swizzling-in-safari-on-mac-os-x%2F&linkname=Method%20Swizzling%20in%20Safari%20on%20Mac%20OS%20X" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F05%2Fmethod-swizzling-in-safari-on-mac-os-x%2F&linkname=Method%20Swizzling%20in%20Safari%20on%20Mac%20OS%20X" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F05%2Fmethod-swizzling-in-safari-on-mac-os-x%2F&linkname=Method%20Swizzling%20in%20Safari%20on%20Mac%20OS%20X" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>

 [1]: http://www.cocoadev.com/index.pl?MethodSwizzling
 [2]: http://www.codethecode.com/projects/class-dump/
 [3]: http://www.fscript.org
 [4]: http://harnly.net/software/letterbox