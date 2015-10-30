.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 BZR.
======
.. contents::

Import existing/init new project.
=================================
::

  $ mkdir proj
  $ cd proj
  $ touch README Makefile main.c
  $ bzr init
  Created a standalone tree (format: 2a)
  $ bzr add .
  adding Makefile
  adding README
  adding main.c
  $ bzr ci -m 'Init proj.'
  Committing to: /cygdrive/e/home/devel/tmp/vcs-bzr/proj/
  added Makefile
  added README
  added main.c
  Committed revision 1.

Cloning/branching repo.
=======================

'branch'/'get'/'clone' are aliases for 'branch' command::

  $ bzr clone proj/ proj-clone
  Branched 1 revision(s).

Updating repo.
==============

Get default remote changes::

  $ bzr update

Update to specific revision::

  $ bzr up -r $REV

Incoming changes.
=================
::

  $ bzr missing --theirs-only bzr://bzr.example.com/proj/trunk

Outgoing changes.
=================
::

  $ bzr st
  modified:
  README
  $ bzr ci -m up
  Committing to: /cygdrive/e/home/devel/tmp/vcs-bzr/proj-clone/
  modified README
  Committed revision 2.
  $ bzr missing --mine-only
  Using saved parent location: /cygdrive/e/home/devel/tmp/vcs-bzr/proj/
  You have 1 extra revision(s):
  ------------------------------------------------------------
  revno: 2
  committer: Oleksandr Gavenko <gavenkoa@gmail.com>
  branch nick: proj-clone
  timestamp: Mon 2011-01-24 00:21:27 +0200
  message:
    up

Working copy status.
====================

'status'/'st'/'stat' are aliases for 'status' command::

  $ bzr rm README
  deleted README
  $ bzr st
  removed:
    README

Show working copy diff.
=======================
::

  $ echo hello >README
  $ bzr diff
  === modified file 'README'
  --- README  2011-01-23 21:16:40 +0000
  +++ README  2011-01-23 21:37:47 +0000
  @@ -0,0 +1,1 @@
  +hello

Show history log.
=================
::

  $ bzr log

Adding files to repo.
=====================
::

  $ touch hello.c
  $ bzr add hello.c
  adding hello.c

Deleting files from repo.
=========================

'remove'/'rm'/'del' are aliases for 'remove' command::

  $ bzr rm README
  deleted README

Undo local changes.
===================
::

  $ bzr rm README
  deleted README
  $ bzr revert README
  +N  README

Undo last commit.
=================
::

  $ bzr add hello.c
  adding hello.c

  $ bzr ci -m bug
  Committing to: /cygdrive/e/home/devel/tmp/vcs-bzr/proj-clone/
  added hello.c
  Committed revision 2.

  $ bzr uncommit
  Are you sure? [y/n]: y
    2 Oleksandr Gavenko	2011-01-23
      bug

  The above revision(s) will be removed.
  You can restore the old tip by running:
    bzr pull . -r revid:gavenkoa@gmail.com-20110123213425-f2ca8umip5iw73is

  $ bzr st
  added:
  hello.c

Info about bzr repo.
====================
::

  $ bzr info
  Standalone tree (format: 2a)
  Location:
    branch root: .

  Related branches:
    parent branch: /cygdrive/e/home/devel/tmp/vcs-bzr/proj

Shelf changes.
==============
::

  $ bzr st
  modified:
    README
  $ bzr shelve --all
  Selected changes:
   M  README
  Changes shelved with id "1".
  $ bzr diff
  $ bzr shelve --list
  1: <no message>
  $  bzr unshelve
  Using changes with id "1".
   M  README
  All changes applied successfully.
  Deleted changes with id "1".

How find most recent tag for current revision.
==============================================
::

  $ bzr tags --sort=time

