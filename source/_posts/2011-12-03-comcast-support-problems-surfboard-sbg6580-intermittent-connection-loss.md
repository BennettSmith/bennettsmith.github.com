---
title: 'Comcast Support Problems &#8211; SURFboard SBG6580 &#8211; Intermittent Connection Loss'
author: Bennett Smith
layout: post
permalink: >
  /2011/12/comcast-support-problems-surfboard-sbg6580-intermittent-connection-loss/
categories:
  - Hardware
---
Last night I finally got fed up with the frequent momentary disconnects that I was experiencing with Comcast. The cable modem/gateway device I have is a Motorola SURFboard SBG6580. I purchased this modem from Amazon after researching which models were supported by Comcast using the information on [this page][1]. Device details are available [here][2]. It is important to note that this is a currently supported option for connecting to the Comcast network.

Here is some information about the modem, as reported by accessing the web interface to the modem.

<pre>Standard Specification Compliant	DOCSIS 3.0
Hardware Version	1
Software Version	<b>SBG6580-3.1.0.0-GA-07-180-NOSH</b>
Cable Modem MAC Address	ff:ff:ff:ff:ff:ff
Cable Modem Serial Number	324369118008466559530006
CM certificate	Installed
</pre>

Looking in the logs of my gateway device I noticed a number of critical error messages. Below is an excerpt of the logs currently on my device. One of the errors that comes up repeatedly is a *T3 time-out*. If you run google searches on this you will learn that many Comcast subscribers (and other cable providers too) see this error in conjunction with intermittent disconnects from their service. 

I have reproduced the log of errors from the modem at the bottom of this post.

After a lot of reading of forum posts on <http://forums.comcast.com> I have learned that many people have similar issues. 

*   [Brief DCs with SBG6580 in Berkeley, CA][3]
*   [Re: Inconsistent connection on Motorola SBG6580 Salem VA][4]
*   [SBG6580 modem problem? or Connection Problem?][5]
*   [Internet Connection Drops off Many Times Daily][6]

What all of these have in common is that after repeated suggestions from Comcast that it was a modem issue or an in-house wiring issue, and after customers in some cases spent money to swap out hardware, none of that helped to resolve the issue. The issue is most likely something *upstream* of the house, but other possibilities exist too.

Some have suggested that the firmware on this model is very old (and riddled with bugs) and that Motorola has made a number of updates to the firmware. You can read an interesting thread about trying to get the firmware upgraded [here][7]. 

I found references to the following firmware versions being available from Motorola to the carriers.

*   SBG6580-3.2.1.0-GA-02-249-NOSH
*   SBG6580-3.3.0.0-GA-06-022-NOSH

Every networking device except a basic switch or hub has firmware in it that can be field upgraded. Most knowledgable customers are aware of this and have probably done at least one firmware upgrade of a networking device. The Motorola SURFboard 6580 is no different. The firmware can be upgraded. The problem is, Motorola will not provide the firmware to end consumers. [Here][8] is a support document from Motorola about their cable modems and the policies about firmware upgrades. To quote, 

> We apologize about the inconvenience, but your Motorola modem does not support manual upgrades. Motorola is not allowed to control the upgrades of DOCSIS devices, per the standards specification. Any firmware or software changes must be implemented via the cable network. Your cable provider can update the firmware based on what they have approved for their network distribution. Because of that Motorola is not capable of installing firmware for cable modems. Please contact the cable operator to obtain information on upgrading firmware on the cable modem. 

Repeated calls to Comcast Customer Service (1-800-XFINITY / 1-800-934-6489) got me no where. I spent approximately two hours on the phone with them. I was disconnected three times, had it suggested to me that the problem was the modem multiple times and was offered the option of paying them for *Signature Support*, but at no time were they able to actually provide me with updated firmware for the modem.

*   They were able to remotely reset the modem.
*   They studied the connection history and noted that indeed the line had been failing intermittently.
*   They were not at all interested in the content of the log messages I shared below.
*   They could not offer any explanation for the log messages.

In summary, they were no help what so ever.

After reading about lack of firmware upgrades and my experience with their customer service folks I began to question whether <t>Comcast Cares(™)</i> about subscribers at all. 

I wonder how many Comcast subscribers have similar problems with intermittent connection loss and just live with it. A survey of forum posts on their own site seems to indicate that the issues are wide spread.

This is truly a terrible situation. Customers purchase devices that Comcast recommends and then when something goes wrong with the service they place all of the blame on the in-house equipment and offer no support what so ever. The cable service providers have things structured such that consumers cannot get support for the devices from the manufacturers because that is the “service agreement” between the manufacturers and cable providers. Customers get squeezed in the middle without any recourse.

According to another site there are [known problems][9] with the Motorola SURFboard, especially with VOIP. I suspect these problems could be addressed with a firmware update, but we have already established that Comcast is in no mood to provide the necessary updates. 

As a last-ditch effort I am now going to place the SURFboard SBG6580 into bridge mode and use a separate router. I found instructions for doing this on Anthony Volodkin’s blog, [here][10]. I will use my Apple AirPort Extreme (which Apple happily provides firmware updates for) as my router. 

In a few days/weeks I will post a follow-up to let people know if this *solved* the intermittent connection loss problems.

* * *

<pre> TLV-11 - unrecognized OID;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Resetting the cable modem due to docsDevResetNow 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 time out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>  
 REG RSP not received;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.0;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.0;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>  
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.0;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>  
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.0;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>  
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing;;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to acquire FEC framing;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:00:00:00:00:00;CM-QOS=1.0;CM-VER=3.0; 
 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 time out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 time out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 SYNC Timing Synchronization failure - Failed to receive MAC SYNC frame within time-out period;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Started Unicast Maintenance Ranging - No Response received - T3 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 Received Response to Broadcast Maintenance Request, But no Unicast Maintenance opportunities received - T4 time out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.1;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>  
 <b>No Ranging Response received - T3 time-out</b>  
 No Maintenance Broadcasts for Ranging opportunities received - T2 time-out;CM-MAC=ff:ff:ff:ff:ff:ff;CMTS-MAC=00:01:5c:24:f1:45;CM-QOS=1.0;CM-VER=3.0; 
 <b>No Ranging Response received - T3 time-out</b>    
</pre>


 [1]: http://mydeviceinfo.comcast.net/
 [2]: http://mydeviceinfo.comcast.net/device.php?tier=-1&devid=268&e=0&d3=1&s=&so=&sc=228
 [3]: http://forums.comcast.com/t5/Connectivity-and-Modem-Help/Brief-DCs-with-SBG6580-in-Berkeley-CA/td-p/1097543
 [4]: http://comcastsupport.lithium.com/t5/Connectivity-and-Modem-Help/Re-Inconsistent-connection-on-Motorola-SBG6580-Salem-VA/td-p/1096399
 [5]: http://forums.comcast.com/t5/Connectivity-and-Modem-Help/SBG6580-modem-problem-or-Connection-Problem/td-p/1058483
 [6]: http://forums.comcast.com/t5/Connectivity-and-Modem-Help/Internet-Connection-Drops-off-Many-Times-Daily/td-p/1045607
 [7]: http://forums.comcast.com/t5/Connectivity-and-Modem-Help/SBG6580-How-to-get-firmware-upgrade/td-p/976719
 [8]: http://broadband.custhelp.com/app/answers/detail/a_id/17811
 [9]: http://www.teltub.com/forum/index.php?topic=45.0
 [10]: http://fascinated.fm/post/2379188731/getting-a-motorola-sbg6580-into-bridge-mode-on
