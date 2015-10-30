.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

================
 gavenkoa tips.
================
.. contents::

About tips.
===========

This site is a collection of tips that author (Oleksandr Gavenko) was
**created** during his life.

Tips licence.
=============

You can do **anything** with these tips. Author take no any warranty.

In countries where defined *public domain* you can think that it was.

**Note** Internetional copyright low (Berne Convention for the Protection of
Literary and Artistic Works, Article 6bis) preserve some non-property (moral)
rights for authors like:

 * author shall have the right to claim authorship of the work
 * author shall have the right to object to any distortion, mutilation or other
   modification of, or other derogatory action in relation to, the said work,
   which would be prejudicial to his honor or reputation

So be careful!

Make HTML version from sources.
===============================

Install docutils package::

  $ sudo apt-get install docutils-common   # for Debian

and build::

  $ make html
  $ sensible-browser tips-html/index.html
  $ sensible-browser tips-html/frame.html

Check sources at::

  $ hg clone ssh://hg.code.sf.net/u/gavenkoa/tips

or browser online at http://sourceforge.net/u/gavenkoa/tips/ci/default/tree/

Make CHM version from sources.
==============================

Install docutils package::

  $ sudo apt-get install docutils-common   # for Debian

and build::

  $ make html

Enter to ``tips-html`` directory and compile with ``Microsoft's HTML Help SDK``.
Under Linux you can use ``Wine`` to run Windows binary.

