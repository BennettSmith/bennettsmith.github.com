---
title: Setting up Unit Testing in Xcode 3.1
author: bsmith
layout: post
permalink: /2008/07/setting-up-unit-testing-in-xcode-31/
categories:
  - Cocoa
  - How To
  - Objective-C
  - Tips from the Trenches
  - Xcode
---
Xcode includes OCUnit, so you don’t need to get a copy. But, you might want to take a look at their website (http://sente.epfl.ch/software/ocunit/) for information and tutorials on how OCUnit is intended to be used. 

If you are planning on doing Test Driven Development (TDD) you may also want to get the following packages:

*   OCMock – OCMock is an Objective-C implementation of mock objects. (<http://www.mulle-kybernetik.com/software/OCMock/>)
*   Hamcrest – library of matchers for building test expressions (<http://code.google.com/p/hamcrest/>)

Other good articles on Xcode Unit Testing that I came across:

*   Unit Testing with OCUnit – <http://www.macdevcenter.com/pub/a/mac/2004/04/23/ocunit.html?page=1>
*   Test Driving Your Code with OCUnit – <http://developer.apple.com/tools/unittest.html>
*   Xcode unit testing articles – <http://chanson.livejournal.com/tag/unit+testing>
*   Unit Testing with Xcode – <http://www.stiefels.net/2007/05/01/unit-testing-with-xcode/>

By reading through the documents references above I was able to get OCUnit up and running for one of my projects. It took a bit of experimentation, but in the end it looks like OCUnit will work just fine for doing TDD in Xcode with Objective-C. Anyone wanting to try out TDD should give it a try. The benefits for your project are significant. Go for it!

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_39">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F07%2Fsetting-up-unit-testing-in-xcode-31%2F&linkname=Setting%20up%20Unit%20Testing%20in%20Xcode%203.1" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F07%2Fsetting-up-unit-testing-in-xcode-31%2F&linkname=Setting%20up%20Unit%20Testing%20in%20Xcode%203.1" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F07%2Fsetting-up-unit-testing-in-xcode-31%2F&linkname=Setting%20up%20Unit%20Testing%20in%20Xcode%203.1" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>