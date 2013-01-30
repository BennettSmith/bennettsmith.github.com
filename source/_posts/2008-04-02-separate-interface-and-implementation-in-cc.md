---
title: Separate Interface and Implementation in C/C++
author: bsmith
layout: post
permalink: /2008/04/separate-interface-and-implementation-in-cc/
categories:
  - C++
  - Patterns
  - Software
---
I spend most of my time developing software in C/C++, and have done so for many years now. One thing that always catches me by surprise is when I find code written by someone who decides to put implementation details of a function or method in a header file. The only reason I can come up with for why developers would do this is pure laziness.

> Let’s face it, C and C++ are such a pain in the but. I mean, each ADT or Class needs two files; a .h and .c/.cpp. It sure would be easier to just lump all the stuff in a single file. Well, since C/C++ can’t generally handle that we might as well sprinkle some of the code into the .h file and some of it into the .cpp file. The compiler really doesn’t care where the code is. And, to top it off, switching between files in most editors takes at least one keystroke. Whoooaaa – what a burden for a busy developer. <img src='http://www.idevelopsoftware.com/wp-includes/images/smilies/icon_smile.gif' alt=':-)' class='wp-smiley' /> 

Of course, this has been written about by numerous people on the web as well as having been covered by many technical journals and books. The concept is to keep the interface in one file and the implementation in another. I am still amazed to find that people routinely place implemenation details in the header files of C++ classes. All this does is **slow down compile times**. Some might say “So what, it doesn’t really matter anyhow. The program still compiles.” Well I say life is too short to spend all your time waiting for the compiler to recompile code that it already compiled, and for which there is no actualy reason to recompile at this point.

It all comes down to dependency management. Developers need to understand how the pieces of their programs interact, how that interaction impacts the build speed for the application, and be aware of techniques they can use to minimize the dependencies between components in their applications.

So, why is it such a bad idea to put implementation details into a header file? There are a number of design principles that would suggest separating interface from implementation pays dividens over the lifetime of an application.

When implementation details creep into an interface header everyone suffers. The compiler has to recompile many more modules each time an implementation change is made. Usually these recompiles are completely unnecessary since all the other modules require is the interface definition from the header file. The problem is that the compiler cannot distinguish an interface change from an implementation change when all of the code is packed into a single header file.

By keeping interface and implementation seperate compile speed will improve. On all but the most trivial projects this is an important thing to keep in mind.

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_21">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F04%2Fseparate-interface-and-implementation-in-cc%2F&linkname=Separate%20Interface%20and%20Implementation%20in%20C%2FC%2B%2B" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F04%2Fseparate-interface-and-implementation-in-cc%2F&linkname=Separate%20Interface%20and%20Implementation%20in%20C%2FC%2B%2B" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F04%2Fseparate-interface-and-implementation-in-cc%2F&linkname=Separate%20Interface%20and%20Implementation%20in%20C%2FC%2B%2B" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>