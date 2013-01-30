---
title: 'GetQueuedCompletionStatus() &#8211; Devil in the Details!'
author: bsmith
layout: post
permalink: /2008/05/attention-to-details-required-when-using-getqueuedcompletionstatus/
categories:
  - C++
  - Microsoft
  - Software
---
One of the projects I work on makes use of the Win32 asynchronous I/O model for managing network traffic between a Windows Service and a custom-built network device. 

One of the key Win32 APIs we use is called GetQueuedCompletionStatus. This API provides access to an I/O completion port that is managed by a separate operating system thread. 

When dealing with this API and Windows asynchronous I/O in general it helps to think about the model as being supported by a separate workpool thread. This API gives the caller a way to synchronize with the operations of that workpool thread (or threads). 

The prototype for this API is as follows:

<pre>BOOL GetQueuedCompletionStatus(
	HANDLE CompletionPort,
	LPDWORD lpNumberofBytes,
	PULONG_PTR lpCompletionKey,
	LPOVERLAPED* lpOverlapped,
	DWORD dwMilliseconds);
</pre></p> 

At first glance the API may not seem too complex. There are 5 parameters and a boolean return type. Some of the parameters are easy to figure out just be looking at their names. Others are less clear. You could speculate that the returned boolean is an indicator of whether or not the operation was successful or not. It is easy to be lulled into a false sense of understanding by reading through the first few paragraphs of the MSDN documentation on this API. 

It actually turns out that this API is very complex (perhaps too complex?), and careful study of the MSDN documentation is required if you wish to handle all of the possible conditions when this API returns. Pay careful attention to the section in the documentation that discusses **Return Values** and **Remarks**. 

My favorite gem from the return values section (and the one I recently missed when using this API) is: 

> If a socket handle associated with a completion port is closed, GetQueuedCompletionStatus returns ERROR_SUCCESS, with *lpOverlaped non-NULL and lpNumberOfBytes equal to zero. 

In other words, when the socket is closed (possibly because the peer closed it) you will get what appears to be a successful I/O completion. This does not represent what most would consider a successful return, and if you have not carefully checked the other parameters, your code may mis-interpret this condition. 

Another area where you need to be careful when using Windows Asynchronous I/O is application shutdown. There may be a number of pending I/O operations that have been queued to the I/O completion port. It is your responsibility to finish processing all of these I/O operations (possibly by first closing the socket and then handling each failed I/O completion event) **and** release any resources that were allocated for the I/O operations. Failing to do this will likely result in a memory leak for the application. 

The moral of the story is to always read the entire MSDN documentation page and make sure your code handles all of the possible combinations of return values!

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_28">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F05%2Fattention-to-details-required-when-using-getqueuedcompletionstatus%2F&linkname=GetQueuedCompletionStatus%28%29%20%26%238211%3B%20Devil%20in%20the%20Details%21" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F05%2Fattention-to-details-required-when-using-getqueuedcompletionstatus%2F&linkname=GetQueuedCompletionStatus%28%29%20%26%238211%3B%20Devil%20in%20the%20Details%21" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F05%2Fattention-to-details-required-when-using-getqueuedcompletionstatus%2F&linkname=GetQueuedCompletionStatus%28%29%20%26%238211%3B%20Devil%20in%20the%20Details%21" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>