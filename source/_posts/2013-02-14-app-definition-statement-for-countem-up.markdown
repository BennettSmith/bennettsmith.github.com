---
# vim: wm=5
layout: post
title: "App Definition Statement for Count'em UP"
date: 2013-02-14 19:53
comments: true
categories: iosweekend
---

Toward the end of March I am teaching an [introductory class in iOS development](http://www.iosweekend.com). Unlike lots of classes that focus on
one API after another, my approach is to walk the students through the creation of a meaningful (dare I say _real_)
application over the course of 2 1/2 days.  As we go step-by-step through the process of creating the application the
students will be developing skills that will serve as a foundation for further independant learning. As a bonus, by the
end of the course the students will have a fully working application on their phone to show their friends.

For the class I needed a meaningful example application. My idea was to build an application that manages one or more
counters. The first things I needed were a description for the idea and a graphic designer to assist with turning that
idea into something interesting and fun to build.  I wrote up an _App Definition Statement_ to describe the application
and searched on [behance.net](http://behance.net) to hire a graphic designer for the project.

## What is an App Definition Statement?

{% pullquote %}
Apple recommends that you create what they refer to as an _App Definition Statement_ to describe each new app you want
to build. As described in the [iOS Human Interface
Guidelines](http://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/MobileHIG.pdf), 
"An app definition statement is a concise, concrete declaration of an app’s main purpose and 
its intended audience. Create an app definition statement early in your development effort to help you 
turn an idea and a list of features into a coherent product that people want to own. {" Throughout development, 
use the definition statement to decide if potential features and behaviors make sense."}"
{% endpullquote %}

## _Count'em UP_ App Definition Statement

The application will let the user easily perform manual counting of many different things.
There are apps like this in the store already so its not an original idea. The idea is easy
for developers to understand and most of their focus will be on learning iOS
development.

The goal is to teach the students to work through the whole process of building an iOS
application. They will be exposed to the process of building something that follows the
graphical and interaction design as spec'd by a professional designer. I'm not just trying
to teach the students to build "programmer interfaces" in iOS applications. I want to
show them how to build beautiful and functional applications. By the end of the class the
students will have an app that they can show their friends and be proud of having built.

The application will have an overview screen where you can see all of your counters in
a colorful display. Perhaps something similar to [Static](http://static.freshbyt.es/) or
[StatNut](http://www.statnutapp.com/). Counters could be grouped together and
assigned a group name. Each group could have a separate overview screen where the
individual counter names and values are summarized. Swipe left/right on overview
screens to get at different sets of counters. Tap on a counter's "tile" to open up the
details of that counter.

Counters would have a name, type and be assigned a color. Depending on the type
there might be other properties too.

Counting up or down might be done using a gesture (swipe up/down) and also by
tapping on a + or - button. Switching between counters might be handled by swiping left/
right. It might be fun to include some sound effects that play on increment, decrement,
reset and when a major boundary is crosses (every 10 counts, for example).
The counters are all stored in the user's iCloud account so they sync between iOS
devices.

### Counter Type: Simple

This is an integer counter. It has a starting value and a step increment. The counter can
be reset manually.

### Counter Type: Target / Goal

This is an integer counter, like the simple counter. The difference is you also set a goal
and the counter displays how close to the goal you are. It might be used to track how
many times you went to the gym this month. This counter type might auto-reset on a
specific date, or might reset manually.

### Counter Type: Elapsed Time

This counter tracks how much time has elapsed. It is basically a stop watch with a
name. The timer can only be started, stopped and reset. When stopped the timer can
be started again to continue measuring time. This might be used to measure the
number of minutes a player is on the field in a youth soccer game. One counter can be
setup for each of the players on the team.

## Example Use Case

Youth soccer coach could setup counters to track game play.
- One elapsed time counter for each player on the team.
- One simple counter for team goal count.
- One simple counter for opponent goal count.
- A way to reset the group of counters should be provided to make it easy to "zero out" before a game.
- When a player is on the field start his/her elapsed time counter.
- When a player is taken off the field stop his/her elapsed time counter.
- When a goal is scored increment the team goal count for the scoring team

