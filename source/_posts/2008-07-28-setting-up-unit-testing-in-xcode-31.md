---
title: Setting up Unit Testing in Xcode 3.1
author: Bennett Smith
layout: post
date: 2008-07-28 08:00
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

