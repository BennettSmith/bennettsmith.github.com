---
title: WinQual Registration Head Aches
author: Bennett Smith
layout: post
date: 2008-03-08 08:00
permalink: /2008/03/winqual-registration-head-aches/
categories:
  - Digital Certificates
  - Microsoft
  - Software
---
In order to digitally sign Windows drivers you need what Microsoft called an Authenticode Digital Certificate. The company I work is creating a number of drivers, so we had a need for an Authenticode Digital Certificate. The certificate would also be used to sign the Microsoft installer packages that we release to customers.

Being a cost conscious group we shopped around and identified two main sources for Authenticode digital certificates.

* VeriSign http://www.verisign.com  
* Thawte http://www.thawte.com

Comparing the prices it seemed clear that the Thawte certificate was a better bet so that is what we purchased. Everything appeared to be fine until we tried to join the WinQual program. That is when I started asking myself the following question:

**Question**: When is an Authenticode Digital Certificate not an Authenticode Digital Certificate?

**Answer**: When you try and use it in the application process for joining the WinQual program.

In the last couple weeks I have been learning about the requirements to digitally sign Windows device drivers. My strategy has been to take the Toaster sample from Microsoft and try to duplicate all of the steps necessary to build a signed version of the driver. Naively, I figured it should be easy to replicate the steps taken by Microsoft to sign this sample program. Boy was I wrong!

It turns out that there is a utility called inf2cat or something like that. Microsoft recommends using it to create the category file containing hashes of the files you want digitally signed as part of your driver package. So, for me to replicate the Toaster sample signing process I need a copy of inf2cat. This tool is apparently only available to members of the WinQual program that Microsoft runs.

Okay, so I need to join WinQual. How hard could that be. I went to https://winqual.microsoft.com and learned that in order to joint he program you must submit a file to them that is digitally signed with your Authenticode certificate. So off I went to get an Authenticode certificate for my company. After a few google searches I came to the conclusion that VeriSign and Thawte are the two primary sources for these certificates, and Thawte is considerably cheaper. I purchased an Authenticode certificate from Thawte and a few days later the certificate was on my machine and it was time to make the membership request on the WinQual site.

I followed all of the instructions to digitally sign the required file using my new Authenticode certificate. Everything seemed to go smoothly until I tried to upload the signed file to Microsoft. Their web site kept saying that the file was not signed correctly. I went back to the main WinQual web page to try and find an answer to this problem. There was nothing there to help me solve this mystery so I went to the only other resource I could think of. That is the DDK mailing list archives at OSR. These folks have been doing Windows driver work for ages and if anyone knew what was wrong, I was sure the answers would be on their mailing list.

It only took one keyword search of the archives to learn what the problem was. It seems that not all Authenticode digital certificates are created equal, and Microsoft has a predilection to those minted by VeriSign. My new Thawte digital certificate would be just fine for signing my drivers, but it would not be at all useful in joining the WinQual program. It was beginning to look like I needed to buy another Authenticode certificate from VeriSign in order to join the WinQual program.

After carefully re-reading the WinQual page describing the ways to join the program I learned that you could also sign your membership request using something called a Corporate Identifier. It was a cheaper, less capable digital certificate that could be used to sign the file and join the program. This certificate could be purchased from VeriSign for $99.

I waited another couple days and the new Corporate Identifier finally appeared in my inbox. I followed the instructions to sign the file, upload it, and this time I met with success in joining the WinQual program.

So, instead of saving money by using the Thawte certificate I ended up spending roughly the same amount of money that it would have cost to just purchase the Authenticode certificate from VeriSign. The difference was that because the WinQual site was not clear on the specific requirements for using a VeriSign certificate I ended up wasting at least 2 or 3 days trying to join the WinQual program.

In the end it was clear that I should have purchased the “name brand” digital certificate from VeriSign.

