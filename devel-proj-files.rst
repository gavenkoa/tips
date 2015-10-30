.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============================
 Development project files.
============================
.. contents::

Additional reading.
===================

 * http://autotoolset.sourceforge.net/tutorial.html
 * https://openide.netbeans.org/tutorial/questions.html

Essential project files.
========================

 * README
 * INSTALL
 * COPYING/LICENSE
 * AUTHORS
 * CHANGES

This files can have suffixes to represent formating syntax:

 * ``.txt`` - plain text
 * ``.rst`` - reStructuredText
 * ``.md`` - Markdown
 * ``.rd``, ``.rdoc`` - RDtool

and optionally compressed - ``.gz``.

README file.
============

Assumed that users first read this file before start using project.

 * Project name.
 * Project goal/purpose.
 * Point to license statements.
 * Point to build instructions.
 * Point to documentations.
 * Use README-xxx for specific topic.

ABOUT/OVERVIEW/SUMMARY file.
============================

 * About project.
 * Use ABOUT-xxx for specific topic.

ABOUT-NLS file.
===============

 * Notes on the Free Translation Project.

NOTES/NOTICE file.
==================

FEATURES file.
==============

MIRRORS/WHERE file.
===================

 * Where get src/build, mirrors list.

PLATFORMS file.
===============

 * Supported platforms and compilers.

AUTHORS/MAINTAINERS file.
=========================
::

  AUTHOR  AUTHORS  MAINTAINERS

 * Was maintained for legal reasons.
 * Regular contributor list.
 * List of project members with contact info (email, phone, home page, address,
   etc).

CONTRIBUTORS/THANKS/CREDITS file.
=================================
::

  CONTRIBUTORS THANKS CREDITS ACKNOWLEDGEMENTS

 * Casual/non-regular contributor list.
 * Wasn't maintained for legal reasons.
 * Thanks for hardware/hosting/money etc.

DEDICATION file.
================

FEEDBACK file.
==============

FORK file.
==========

 * Why this project is fork of another project.

COMMANDS file.
==============

 * brief list of commands for built-in language

PROGLIST file.
==============

UPGRADE/UPGRADING/CONVERSION file.
==================================

 * How upgrade to new version.

SERVICE/SUPPORT file.
=====================

 * about support services for software

INSTALL/BUILD file.
===================

 * List of supported platform.
 * Build dependencies/prerequisites.
 * Build/installation instructions.

CUSTOMIZE file.
===============

 * Customize the compilation.

License files.
==============

DISCLAIMER file.
----------------

PATENTS file.
-------------

TRADEMARK file.
---------------

COPYING/LICENSE/LEGAL file.
---------------------------

COPYING usually used for GNU GPL like license. Another license put in LICENSE
file.

If some component comes with different license put it into file with name like::

  LICENSE.libmy LICENSE.regex LICENSE.doc
  COPYING-DOCS  COPYING-GPL   COPYING-LGPL  COPYING-LIBS  COPYING-TEMPLATES
  COPYING.LESSER

COPYRIGHT file.
---------------
::

  copyright
  COPYRIGHT
  copyright-artwork
  copyright-notice

AFL file.
---------

Academic Free License.

  AFL-1.1
  AFL-1.2
  AFL-2.0
  AFL-2.1

 * http://www.opensource.org/licenses/afl-3.0.php
 * http://en.wikipedia.org/wiki/Academic_Free_License

Apache file.
------------
::

  Apache-1.0
  Apache-1.1
  Apache-2.0

PHP file.
---------
::

  PHP-3.0

MIT file.
---------
::

  MIT  LICENSE_MIT

BSD file.
---------
::

  BSD  LICENSE_BSD

GPL file.
---------
::

  GPL-2    GPL2
  GPL-2.0
  GPL-3.0  GPL3
  LICENSE-GPL

LGPL file.
----------
::

  LGPL-2   LGPL-2.0  LGPL-2.1  LGPL-3.0  LICENSE_LGPL
  COPYING.LESSER

Developer files.
================

HACKING/DEVELOPERS/PORTING file.
--------------------------------

 * Notes for developers.

CONTENTS file.
--------------

 * Description which file for which comes.

CONTRIBUTE file.
----------------

 * Guidelines to contribute to the project.

::

  CONTRIB
  CONTRIBS
  CONTRIBUTE
  Contributing
  HOW-TO-CONTRIBUTE

DEBUG/DEBUGGING file.
---------------------

 * How debug sources, useful macros/function/tips.

DESIGN/INTERNALS/PROTOCOL file.
-------------------------------

TESTS/CHECK_NOTES file.
-----------------------

 * How run/add tests, requirements to run.
 * How and when test passed by which platform/configuration.

BINDINGS file.
--------------

 * Known bindings of library to different langs/frameworks.

Coding style files.
-------------------
::

  C++STYLE
  CodeStyle

CODING file.
------------

 * project policy and recommendation on coding

CONVENTIONS file.
-----------------

Project changes files.
======================

Here goes news and descriptions of user visible changes:

 * Important project news.
 * New features.
 * Obsolescense/deprecation of UIs/APIs/protocols/formats.

ChangeLog file.
---------------

 * Changes made to program source files.
 * Explains how earlier versions were different from the current version.
 * Each directory can have its own change log.
 * Useful for RCS/CVS. Don't needed with modern VCS (SVN, Git, Mercurial, Bazaar).

::

  changelog  Changelog  ChangeLog
  CHANGELOG
  ChangeLog-1996-1999   ChangeLog-2000
  ChangeLogOld

COMPAT/COMPLIANCE file.
-----------------------

 * Compatibility with previous versions.

NEWS/OLDNEWS/ONEWS file.
------------------------

 * User-visible changes.
 * In each new release, add items to the front of the file and identify the
   version they pertain to.
 * Don't discard old items.
 * NEWS file gets very long, move some of the older items into a file named
   ONEWS and put a note at the end referring the user to that file.

CHANGES/WHATSNEW file.
----------------------
::

  Changes  CHANGES  CHANGES-release
  RELEASE_NOTES  ReleaseNotes  RELEASENOTES  RELEASE-NOTES
  RELNOTES
  SHORTLOG
  WHATSNEW

ANNOUNCE file.
--------------

Todo files.
===========

 * List of high level wanted, general project roadmap.
 * Discussion about product limitations and how to modify product to resolve
   them.

Similar::

  BACKLOG
  CHECKLIST
  TODO
  PROJECTS

PROGRESS file.
==============

Version info files.
===================

VERSION file.
-------------

 * Package version.
 * Package name (optional).
 * Release naming schema and version number semantics (optional).
 * Release names and version relations (like starts, toys, animals, etc, optional).

RELDATE/RELEASE-DATE file.
--------------------------

ANNOUNCE file.
--------------
::

  ANNOUNCE
  ANNOUNCEMENT

 * Only current release changes and notes. No history. Same text was sent to
   mail lists as announce.

HISTORY file.
=============

 * Project history in long perspective.

FUTURE file.
============


Documentation files.
====================

USAGE file.
-----------

Refcard files.
--------------
::

  cheatsheet
  refcard

FAQ files.
----------

 * List of frequency asked questions with answers.

TIPS/HINTS file.
----------------

HOWTO file.
-----------

PROBLEMS/KNOWNBUG/WARNINGS file.
================================
::

  PROBLEMS
  KNOWNBUG  KNOWN_BUGS  KNOWN-BUGS
  WARNINGS

Bug report instructions.
========================
::

  BUGFORM
  REPORTING-BUGS
  BUG-REPORTING
  BUG-REPORTS
  BUGS

BINDINGS file.
==============

Reference.
==========

  /usr/share/doc/common-licenses/*
                from Cygwin 'base-files' package, list of licence files

Unknown files.
==============
::

  AUDIT
  DETAILS
  FILE-FORMAT
  Fixes
  FIXES
  FORMAT
  MAIL
  NEEDED
  PGPKEYS
  PKG-INFO - http://www.python.org/dev/peps/pep-0241/ http://www.python.org/dev/peps/pep-0314/
  PLACES
  ROADMAP
  TRACING

Reference.
==========

 * GNU Coding Standards
 * Gnits Standards

