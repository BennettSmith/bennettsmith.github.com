---
# vim: textwidth=78:wrapmargin=5
layout: post
title: "Setup a git server on Mac OS X"
date: 2013-01-04 11:02
comments: true
published: false
categories: 
---
I have been looking for a good way to distribute sample code in some iOS workshops that are
coming up.  My requirements are simple:

* I want to manage the code using git.
* I want to _backup_ the code to a private GitHub repo for safe keeping.
* I want the students to access the code by cloning a git repo in the classroom.
* I don't want the code to be publically accessible on a hosted services like GitHub.

To achieve these goals I decided to setup a git server running on my laptop.
This will let me keep the main version of the code in GitHub and push to the
private repo on my laptop when appropriate.

I plan to push changes to the repo using __SSH__ and let the students clone
from the repo using the __HTTP__ protocol. Students will have annonymous
access to the repo, but it will be read-only access.

To setup a git server I consulted the book [_Pro Git_](http://git-scm.com/book), 
written by Scott Chacon and published by Apress.  

## Add _git_ user

In the book Scott suggests using the ``adduser`` command to create a new user
called _git_.  On Mac OS X the following commands are used to create a new
user from the comamnd-line:


## Add _git-ro_ user


