---
layout: post
title: "Plugin Experiments"
author: Bennett Smith
date: 2013-01-29 22:47
comments: true
categories: 
---

### GraphViz

{% graph non-directed graph %}
a -- b
b -- c
c -- a
{% endgraph %}

### SpeakerDeck

{% speakerdeck 5112451026bf013092b722000a1d8877 %}

### AppStore

This plugin does not seem to work. I think the format for the URL in the AppStore may have changed and the plugin needs to be updated.  Need to investigate this one further.

{% app_store 364709193 %}

### Video Tag

This does not seem to be working right now.  I think the link might be broken.

{% video http://s3.imathis.com/video/zero-to-fancy-buttons.mp4 640 320 http://s3.imathis.com/video/zero-to-fancy-buttons.png %}

### Image

{% img http://placekitten.com/890/280 %}

