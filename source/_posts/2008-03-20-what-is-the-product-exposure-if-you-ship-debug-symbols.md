---
title: What is the product exposure if you ship debug symbols?
author: bsmith
layout: post
permalink: /2008/03/what-is-the-product-exposure-if-you-ship-debug-symbols/
categories:
  - Software
---
At some point in the life-cycle of a product being developed it seems like every team ends up trying to decide if they should ship debug symbols with their product. On one side of the discussion are people who perceive that the crown jewels of the company are somehow at risk if the symbols escape from their office. On the other side of the discussion are people who perceive that having matching debug symbols delivered with the shipping product will help with solving the inevitable problems that arise in the field.

So, who is correct here? How much of a risk is there in shipping debug symbols?

My own opinion is that shipping the debug symbols for a release build of a product presents a very small degree of risk. I feel that anyone so inclined can reverse-engineer your product from the shipping executable files, and not having symbol information will not deter them. It may slow them down slightly, but not by a sufficient amount to warrant not shipping symbols.

Since this topic comes up so frequently I figured I would try and collect together various other points of view on the question. First stop; Google!

The quote below is from the project page of the [CrashRpt][1] library, found on the Google Code service.

> I’ve received several comments/inquiries about shipping debug builds or debug symbols. You should never ship debug builds or debug symbols as they will not only take up more space on your CD/download/client’s workstation, but they will also make reverse engineering your code a trivial exercise. To be clear, what I’m suggesting is modify your release build configuration so that it generates debug symbols, saving both the release builds of your modules and their corresponding debug symbols in your source control system and delivering only the release builds of your modules to clients (as you do today). When a crash report comes in, you use the release build and debug symbols you archived, along with the minidump included in the crash report, to debug the crash. 

Microsoft had published a technical article titled [Generating and Deploying Debug Symbols with Microsoft Visual C++ 6.0][2] that goes through some of the options when consdiering if shipping debug symbols is appropriate for your product. From the article …

> The first thing you have to do is determine whether you should deploy your debug symbols. In general, you should deploy symbols during most of your internal testing. This will give you better information to track down bugs. But before you deploy debug symbols to your customers, you should consider whether you want them to have access to that level of information about your application and whether they have the extra storage space. You also need to consider the type of customer you are targeting. Many software developers like to have debug symbols. Many end users would rather not use up their hard drive space for something they are unlikely to use.
> 
> For instance, Windows NT deploys debug symbols with the operating system. These symbols contain primarily function-level symbols and FPO records. Microsoft Office does not deploy debug symbols. 

And then later in the same article…

> Deploying debug symbols does not affect the performance or initialization of your application, but does impact available hard drive space. Debug symbols can take up some significant hard drive space, depending on the granularity. 

Another terrific article I came across is [Release Mode Debugging][3], published by ACCU in their **Overload Journal**. I would recommend reading the entire article to gain some perspective on the idea of having a single build for your product instead of separate debug and release builds.

The argument against shipping debug symbols is often that this will make it easier for competitors to gain access to the intellectual property that you hold so dear. While it is true that having the debug symbols (especially for internal private structures) will make the process of reverse engineering your software easier, it by no means prevents it. The application [IDA Pro][4] is a commercial disassembler and debugger that would make reverse engineering of any application possible. They call it *The most advanced tool for Hostile Code Analysis, Vulnerability Research and Software Reverse Engineering*.

Further evidence that a lack of debug symbols is no protection against reverse engineering comes from the article [Reverse Engineering Hostile Code](), published on the SecurityFocus web site. Anyone who believes that hackers are thwarted from decompiling or reverse engineering your software because they don’t have symbol information will surely change their point of view after reading this article.

In the end, it seems like shipping debug symbols or not is more a “feel good” issue for an organization than it is a way to actually address a security concern.

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_20">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F03%2Fwhat-is-the-product-exposure-if-you-ship-debug-symbols%2F&linkname=What%20is%20the%20product%20exposure%20if%20you%20ship%20debug%20symbols%3F" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F03%2Fwhat-is-the-product-exposure-if-you-ship-debug-symbols%2F&linkname=What%20is%20the%20product%20exposure%20if%20you%20ship%20debug%20symbols%3F" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F03%2Fwhat-is-the-product-exposure-if-you-ship-debug-symbols%2F&linkname=What%20is%20the%20product%20exposure%20if%20you%20ship%20debug%20symbols%3F" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>

 [1]: http://code.google.com/p/crashrpt/
 [2]: http://msdn2.microsoft.com/en-us/library/aa260783(VS.60).aspx
 [3]: http://accu.org/index.php/journals/1412
 [4]: http://www.hex-rays.com/idapro/