---
title: 'You can&#8217;t keep a good class library down &#8230; MFC gets reprieve from death sentence!'
author: bsmith
layout: post
permalink: >
  /2008/07/you-cant-keep-a-good-class-library-down-mfc-gets-reprieve-from-death-sentence/
categories:
  - C++
  - MFC
  - Microsoft
---
A few years ago I was working at a company where we built applications using Visual Studio 6 and MFC. The applications had been around for about 10-12 years, and were all showing their age. Customers were beginning to request updated user interface features like they were seeing in *modern* Microsoft products such as Office and Internet Explorer. Sadly, we could not deliver these user interface enhancements easily because MFC was not getting any attention from Microsoft.

In late 2002 Microsoft was pushing the .NET Framework, C# and WinForms as the heir apparent for Win32, C++ and MFC. Converting a decade of legacy C++ MFC code to .NET and WinForms just wasn’t an option. We all felt like Microsoft had just abandoned us for greener pastures.

Our solution at the time was to start a long difficult process of moving away from MFC toward a cross-platform class library built by [Trolltech][1], called Qt. In many respects this turned out to be a good decision since it meant we could begin to seriously consider offering our applications on Windows, Linux and the Mac instead of just on Windows. Still, it felt like Microsoft had hung us out to dry.

The WinForms classes just were not rich enough to build complex desktop applications at the time. Many of the conveniences we had come to rely upon from the MFC class libraries were missing and it would have been up to us to roll our own alternatives had we gone down the WinForms route. I think Microsoft was too focused on building web applications to devote sufficient resources to WinForms.

Here we are six years later and Microsoft has announced that they are providing a *MFC Feature Pack for Visual C++ 2008* that will add significantly to the capabilities of the MFC class libraries. I can hear MFC development teams all across the Internet celebrating this change in stance from Microsoft.

Here are a couple links to information from Microsoft on the topic:

*   [MFC Feature Pack for Visual C++ 2008][2]
*   [Pat Brenner: New Updates to MFC in Visual Studio 2008][3]

Couple MFC with a good third-party widget library like the toolkit offered by [CodeJock Software][4] and you have everything necessary to build some awesome new desktop applications.

**Long Live MFC!**

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_37">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F07%2Fyou-cant-keep-a-good-class-library-down-mfc-gets-reprieve-from-death-sentence%2F&linkname=You%20can%26%238217%3Bt%20keep%20a%20good%20class%20library%20down%20%26%238230%3B%20MFC%20gets%20reprieve%20from%20death%20sentence%21" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F07%2Fyou-cant-keep-a-good-class-library-down-mfc-gets-reprieve-from-death-sentence%2F&linkname=You%20can%26%238217%3Bt%20keep%20a%20good%20class%20library%20down%20%26%238230%3B%20MFC%20gets%20reprieve%20from%20death%20sentence%21" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F07%2Fyou-cant-keep-a-good-class-library-down-mfc-gets-reprieve-from-death-sentence%2F&linkname=You%20can%26%238217%3Bt%20keep%20a%20good%20class%20library%20down%20%26%238230%3B%20MFC%20gets%20reprieve%20from%20death%20sentence%21" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>

 [1]: http://www.trolltech.com
 [2]: http://msdn.microsoft.com/en-us/library/bb982354.aspx
 [3]: http://channel9.msdn.com/posts/Charles/Pat-Brenner-New-Updates-to-MFC-in-Visual-Studio-2008/
 [4]: http://www.codejock.com/