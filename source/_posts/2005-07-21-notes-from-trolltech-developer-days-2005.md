---
title: Notes from Trolltech Developer Days 2005
author: Bennett Smith
layout: post
date: 2005-07-21 08:00
permalink: /2005/07/notes-from-trolltech-developer-days-2005/
categories:
  - Software
---
Class: Introduction to Qt Programming  
Instructor: Robert Hartley (rhartley@ics.com)

Send Robert an e-mail requesting a copy of the “C++  
Programming for Qt” presentation.

Breakfast – Scientific Toolworks

Send e-mail asking for a copy of full week notes PDF file.

Enhancement for Qt 4.1  
======================  
Qt Designer 4.1 will have a menu editor and a toolbar  
editor.

Observation about QMake  
=======================  
People are confronting issues with their existing build  
environments and how to integrate qmake into that. At least  
one person indicated that he feels like it is necessary to  
give up some of the nice things in qmake to use his build  
system. Likewise, if he uses qmake then he gives up other  
things that are relied upon as part of their environment.

Possible Bug  
============  
Build the connect example.  
Run it.  
Maximize using the box in the upper right corner.  
Double-click the caption bar to restore the regular size.  
The window restores and then immediately maximizes again.  
Then double-click again and it restores properly.  
It should restore on the first double-click.

Qt 4.1 Release  
==============  
Expect a release by the end of the year.

Whirlwind Tour through Qt  
=========================

QWidget can be used as an invisible container for a group of  
widgets.

No current replacement for a canvas. Use Q3Canvas for now.  
There will be something new coming in Qt 4.1. (Scene Graph)

Missing Widgets & Components  
============================  
No rfc822 e-mail components to manage messages or to talk  
with POP3, IMAP, or SMTP servers.

No good “outlook bar”-like widget.

In general the look and feel of the widgets is like the old-  
style windows controls. There does not appear to be any  
support for the new Windows XP themes.

Toolbar support is weak. No indication of the drop zone for  
the toolbar. It doesn’t float either. I’m also not sure if  
the toolbar supports alpha-channel graphics like Windows XP.

Book Update  
===========  
A version of the book for Qt 4 will be available early next  
year. It will be by the same authors.

Missing Resources  
=================  
Emphasis is on widgets for GUI design. It would be nice to  
see topics like in the Petzold book that discuss the  
fundamentals of the painting model, events, window  
creation/lifetime, etc. There might be room for a book or  
set of training materials on this. Something like the “MFC  
Internals” book might also be nice to have. Event routing /  
keyboard focus. These are mysterous also.

Questions  
=========

Q. How can we route QActions to the proper destination. For  
example, the Edit menu can contain actions for Copy, Cut,  
and Paste. These operations should be routed to the  
currently active widget. If the QActions are hooked up to  
the main window they will not go to the correct destination.  
I suppose you could remap the actions each time the focus  
changes, but this sounds like a brute-force way to  
accomplish this.

A.

Q. Does Qt have a font fallback mechanism?

A. Yes – this is provided by Qt directly since there is no  
reliable fallback mechanism that works across all platforms.

Q.

Global Event Filters  
====================

Shoot a Bug

Install a global event filter to dump object information.

// Place before call to app.exec();  
qApp->installEventFilter(new ShootABug());

The Filter class

class ShootABug : public QObject  
{  
public:  
virtual bool eventFilter(… recv …)  
{  
if (event->type() != QEvent::MouseButtonPress)  
return false;  
QMouseEvent* event = static_cats…  
…

// Old way  
qDebug() <objectName().local8Bit();

// New way  
qDebug() <objectName());

qDebug() <metaObject()->className();  
qDebug() <dumpObjectInfo();  
qDebug() <dumpObjectTree()  
}

repaint() is evil  
=================

Do not \*\*ever\*\* call repain() yourself. You should be  
calling update() instead. It will handle painting properly  
on all platforms. Update() will invalidate the entire region  
of the widget.

Visual Studio Debugger  
======================

Add to Common7\Packages\Debugger\Autoexp.dat to display  
QString in the Visual Studio Debugger.

; from Qt  
QString=data,su>

CEO “Key-note” Presentation  
===========================  
Minimize risks  
Future-proof your efforts by using Qt  
Support for Vista is being carefully followed.  
Dual-license also helps minimize risks – source code is  
always available.

All developers at Trolltech are “just like every other  
developer” – they work in offices!

What happened in last 12 months?  
* Grew from 80 to 140 people in 12 months  
* Profitable  
* Second round of funding  
* Established China office  
* Released Qt4

Qt 4 under development for 2 1/2 years.

Next 12 months – what to expect?  
* Professional service organization  
* Chief Technical Officer

Increasing demand for professional services is seen.  
Trolltech is creating a professional services organization.

“Code Less. Create More” — don’t forget that developing  
software should be fun. If development is feeling like a  
slog through the mud then do something different.

Powerful frameworks will help — Qt is such a framework.

UI – Rich or Thin?  
* “You can never be too rich or too thin”  
* QT/COCO -  
– Thin client technology for Qt  
– Install any Qt application on a server  
– Deploy thin, universal client in organization  
– Targeted at enterprise deployment  
– Prototype stage  
– Amazing performance 10x faster than X

This seems kind of like their answer to .NET framework  
ASP.NET thin clients or Java clients.

QT Java Technology  
* Qt/Java bindings  
* Lets java developers use Qt APIs from java env.  
* Under development  
* Prototype Q1 2006

Qtopia Update  
- Defacto linux standard  
- 85 manufactures building linux devices with qtopia  
- 30 mobile phone man. building linux phones  
- linux is a disruptive force in the handset industry  
- trolltech goal: 100M phones by 2008

Qtopia 4 platform coming  
Qtopia 4 Phone Edition PDA edition

What’s new in Qtopia 4?  
- Rich feature set of Qt4  
- Qtopia 4 highlights  
– safe exec. environment – native sandboxing  
– integrated SQL database on every device  
– advanced graphics, themeing etc. to customize UI

=========================================================

Qt 4 and Beyond  
Matthias Ettrich, VP Engineering

Qt History – 10 years of enabling cross-platform  
- Issolate your code from operating system code.

Qt Evolution  
- Mac is very active platform – driving some changes in Qt 4  
- Vista – Avelon  
- Office 12  
- Linux – kde

Qt 4 Design Goals  
- Enhanced capabilities  
- Greater flexibility  
- Solid foundation for future  
- while retaining a large degree of comapatibility

Qt 4.0 – The good  
- Cusomters and users value the new functionality  
- Clean codebase allows us to turn around quickly  
- Quick adoption in the Open source world  
- Successful and fast ports from Qt 3

Qt 4.0 – The Not So Good  
- A .0 release is a .0 release  
- Some users expressed dissatisfaction with the performance  
of certain painting operations  
- qt3to4 and Qt3Support library partially failed to deliver  
- Qt Designer lacked action editor

Qt 4.1 – The answers  
- Many small bug fixes and imporovements, based on tcustomer  
feedback (Task Tracker)  
- Painting optimizations, including hadrware acceleration  
using OpenGL  
- Highly improved and extended Qt3Support module  
- Enhanced Qt Designer with action editor

4.1 is nearing freeze now. Should be available sometime  
after the Munich dev days event.

Qt 4.0 – Arthur  
Can render SVG!  
Can do native rendering to PDF also!

Qt 4.x Priorities  
- Accomodating Microsoft Visat  
– Scene-based graphics  
- Improving Embedded and Mac  
- Bug fixes, performance improvements  
- Further improvements in At 3 ato Qt 4 migration experimnce  
- New features according to customer needs

Examples  
– Raising abstraction level for dialogs  
– Desktop integration (local browers, local help system,  
system tray, etc.)  
– Higher main window abstraction (MDI, SDI abstraction for  
example)  
– More widgets  
– Help system – framework for context help not there yet.  
– Deployment issues – instalers  
– Component model

THere are many many things they can do. Not sure which ones  
they are actually going to address in Qt 4.x.

Q/A

- Some solutions not ported from Qt 3 to Qt 4  
- In Qt3 you could put widgets in a menu. In Qt 4 this is  
not possible. in Qt 4 a more general approach is coming, but  
not ready yet.

=========================================================

3/4 billion hand-sets sold

productivity is key – need access to your data from portable  
devices when/where you want.

Qtopia can help bring this level of access to consumers.

New mobile devices have significant headroom for doing other  
things (beyond email/pim, sms, operating system, telephony).  
This is important to recongize. Smart phones are going to be  
very, very smart.

Expect VGA screens, video recorders, high-end audio, 3MP+  
cameras, security, games, etc.

Development of enterprise applications that can run on these  
devices.

Designing for the Future  
========================  
Things are getting more conneted (dhu!) Consumers expect  
devices to be always connected. They will be smaller,  
lighert, longer life. They will have more MIPS. Better,  
faster, cheaper.

=========================================================

Qt @ Synopsys  
How Synopsys Creates the Best GUIs in EDA

need to focus on how to create consistent (common) look&feel  
across applications becomes critical.

Distinguishes yourself.

Microsoft Office is an example of this. All pieces use  
common UI idioms.

Overview  
- Consolidation is Driving the Software Industry  
- A Short Primer on Common Look and Feel  
- How Synopsys Uses Qt to Achieve the Best GUIs in EDA

Consolidation in the Software Industry  
- customer want less complexity  
- don’t want to build their own mosaic  
- don’t want to buy each title

There is demand for complete easy to use solutions

Prodblems Brought on by Consolidation  
- Diverse appliations used together to solve a larger  
problem.  
S

What is Common Look & Feel?  
- Multiple Products working together.  
– Example is Apple (iPod, iBook, mac mini) – They get  
consistency for user experience  
- Global Optimization for Common Tasks  
– Adobe is a good example with the Creative Suite  
of products. Color selection, layers, etc. are all  
handled the same way. Learn once, apply everywhere.  
- Conscious Commitment to Cross-Product Design  
– Conscious application of systematic design methods to  
a set of products, components, or modules so as to  
maximize their mutual consistency and compatibility  
with one another in support of the designated user and  
task domain. It is the methodology through which  
common look & feel is achieved.

Synopsys  
– Over 1600+ R&D engineers  
– Over 60 offices  
– Over 350 account managers  
– Over 1450+ applications engineers

System Design  
Functional Verification  
Synthesis  
Physical Implementation  
Manufacturing Prep.  
IC Test

Driving Principals:  
– Focus on product suites drive GUI convergence  
– Complexity of IC design drives visual innovations

Background  
– prior to 2001 used MFC for GUI development  
– used porting packages to move to Unix

problems  
– Stability, sensitive to OS patches, high support costs  
– Extendibility , poor modularity and object-oriented  
design  
– not portible, no 64-bit support, no linux support  
– performance, sluggish GUI and graphics performance

We had to find alternative technologies!

So, what GUI technology should we use?  
– Java  
– Motif  
– Tcl/T  
– Gnome  
– Qt

Were excited about Java, but performance was a problem.

Qt was the solution!  
- Performance  
- Platform Support  
- Compatibility C/C++  
- Supply of Developers  
- Object Oriented, modular, extendable  
- Powerful Widgets  
- Short Learning Curve  
- Quality & Support  
- Long Future Lifetime

———-  
How di Synopsys deliver common look & feel?  
- Created EDA specific GUI framework with Qt as the  
foundation  
- Reusable highlevel components & plumbing  
- Specialized centeral organization, distributed product  
focus  
- Requirements driven by products  
- User centered design  
- Structured development methodology.

Qt Components  
- Windowing  
- Tcl Console (they have scripting!)  
- Menus/Toolbars  
-Application Services

Synopsys GUI Organization  
Pros:  
- UI principles promoted from within product team  
- UI reps maintain ties and loyalty to corporate goals  
- UI reps can pull in outside expertise when needed

Cons:  
- Requires maturity from management to resolve conflicts

Did it work? Yes!  
- Gains in efficiency & quality through code reuse  
- Lots of commonality comes for free  
- Designers have more time for unique problems  
- Time to market shorter  
- Common code is practially bullet proof

Qt quality enabled innovation in Visualization!

Feeling is that Synopsys offers superior visualization  
technology for the EDA customer.

State of the art for chip designers hasn’t really changed  
much. (VT100 then –> VT100 terminal emulator window now)

The Visual Information Seeking Mantra:  
- Overview first,  
- Zoom and filter,  
- Then details-on-demand.”

Ben Shneiderman

Modern Screen resolution and graphics per. allow this.

Advantage of Qt  
- Portable across multiple OS config.s  
- High quality  
- Powerful, flexible and extendable building blocks

Conclusion:

Qt provided Synopsys with a complete, high quality  
foundation  
Synopsys exploited Qt object oritned design  
Resulting in:  
– increased productivity and quality  
– common look & feel across product suites  
– focus on innovative visualtiy

Lunch Session  
================  
Scott Collins  
scc@trolltech.com

User interface ideas

Put the user in control  
- scriptability  
- plug-ins  
- emulation  
- dynamic interface  
– toolbars  
– user assigned short-cuts  
– user menus  
– user dialogs

Think about the problem you are trying to solve in terms of  
a language. Make it possible to express your solution. This  
is a clarifying way to learn about the problem and solution.

Fit the user’s world  
- import/export  
- scriptability, nternal  
- scriptability, external/system  
- plug-ins  
- special features of the OS

Make sure that the user can fit your application into their  
world. Install/uninstall as expected on each OS. Use  
desktop search capabilities to index your application data  
on each platform (Spotlight on Mac, WinFS on Vista, Google  
desktop Search?)

Use the Network  
- check for updates  
- report crashes  
- on-line help  
- collaboration  
- information from the web

The user community – Transparency  
- public forum  
- public bug database  
- public policies  
– privacy  
– security  
– support  
- blog

Consider Open Source  
- Ccan it fit your licensing model  
- can it fit your development model  
- can you cross the chasm to community interests

Listening  
- making it obvious  
- making it easy  
- what to do with input  
- showing the user you’ve heard

We are good at creating develoment tools because we are the  
users. Listen to the users and then any tool can be as good  
as development tools. The users know what they want, but  
sometimes they say things that are crap/wrong. You must  
separate the good from the bad.

User not using just your program, but also using your  
company. Establishing an on-going relationship with you and  
your company. What you give them should reflect your  
understanding that this is a partnership.

================================================

Threaded Programming – Good Practise  
Andreas Aardal Hanssen

Handout contains examples of threading programming model.  
Kind of like MVC, but for threading.

\***| Latency is the enemy, concurrency is king.

Writing threadable code  
- allow objects to live in separate threads, and to be  
used from a different thread  
- write reentrant (or thread-safe) code?  
– preferably no statics  
– standalone objects  
- prefer “reentrancy” over thread-safety

Concurrency is Kin  
- avoid locks where possible  
- lock data, do not lock code  
- free the lock as soon as possible

Lock data, not code  
bad  
mutex.lock()  
words[0].append(“-example.txt”);  
mutex.unlock();

good  
mutex[0].lock();  
words[0].append(“-example.txt”);  
mutex[0].unlock();

Good Threading Models  
- The lazy worker thread (P-C)  
- The single-shot task thread  
- The upside-down parser thread  
- (The extra event loop thread)  
- (The render-ahead thead)  
- (Someone should write a book)

The single-shot task thread  
- Gets job description from the constructor  
- Performs the task immediately in run()  
- Emits done() when done, then exits.

See handout: DataWriter::DataWriter(), Run()

Look up the thread-function adapter design pattern.

The upside-down parser thread  
- A parser in the run() function  
- Calls getChar(), blocks when out of data  
- The parser is “fed” from the main thread through a  
public feed() function  
- Basically P-C in different wrapping

See handout: Tokenizer::feed(), getchar()

Check out QThreadStorage if you want to manage heap more  
efficiently across threads.

===============================

Practical Model View Programming  
Marius Bugge Monsen

Most slides are figures – difficult to take notes – ask for  
a copy of the slides.

Qt 4.1 will have proxy models. This permits sorting and  
filtering to be implemented easily on a per view basis  
without effecting the source model.

In Qt 4.x (4.2 or some other future version) it could be  
possible to aggregate multiple source models into a single  
proxy model.

It would be nice to see an example of a sliding-window model  
that handles looking at n items before/after the current  
window of items. Not sure if this is possible. How would  
this work with views that want to display all items? Is  
there a way to know what the maximum number of items that  
can be displayed in the view is? This would constrain how  
much data must always be present in the sliding-window  
model.

Qt 4.1 should probably be available in next 1-2 months.  
Qt 4.2 is scheduled for late in the first 1/2 of 2006.

=======================================

Writing Plugin Applications with Qt  
And Customizing Qt and Qt Designer

Qt 4 introduces a general framework for writing plugin  
applicaitons

Examples  
- plug & paint applicaiton  
- .cur image handler  
- tic tac toe widget

Next year the offical trolltech Qt 4 book will come out.

Example of .pro file for qmake to build a plugin.

TEMPLATE=lib  
CONFIG += plugin  
INCLUDEPATH += ../..  
HEADERS = …  
SOURCES = …  
TARGET = plugin_name  
DESTDIR = ../../plugandpaint/plugins

No equivalent way to build a plugin from within Visual  
Studio .NET (yet?)

=================================================

All About Widgets  
The QWidget 4.1 API In Depth

QWidget’s API is complex  
- 254 documented functions  
- 53 properties

Many features are poorly understoon

Qt 4.1 introduces some new features:  
- backing store  
- application modality

Window Properties  
- setWindowTitle  
- setWindowIcon  
- SetWindowIconText  
- setWindowModified  
- isWindow, window

No QWindow class – just some QWidgets are actually windows.  
Functions with “window” in the name are for these “special”  
widgets.

Window Flags

Influence the look/feel of the window  
- only make sense for top-level widgets/windows  
- consists of window type and zero or more hints

Widget Attributes  
- boolean properties  
- setWidgetAttribute(…)  
- testWidgetAttribute(…)

examples of attributes….  
- Delete on close  
- Mac Metal style  
- Hover  
- Contents propagated

Widget Geometry

Q – Does window geometry handle multiple displays well?  
Q – Does window geometry handle different dpi well? Looks  
like arguments are specified in pixels.

