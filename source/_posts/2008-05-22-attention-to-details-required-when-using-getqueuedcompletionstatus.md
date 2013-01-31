---
title: 'GetQueuedCompletionStatus() &#8211; Devil in the Details!'
author: Bennett Smith
layout: post
date: 2008-05-22 08:00
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

