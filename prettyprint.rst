.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========================
 Pretty print source code.
===========================
.. contents::

About pretty printing.
======================

Code formatter, beautifier, pretty printer.

  http://en.wikipedia.org/wiki/Pretty-printer
                Wiki article.

xml.
====

tidy.
-----
::

  $ tidy -xml -i -utf8 -o out.xml in.xml

or in Emacs::

  C-x h C-x <RET> c utf-8 <RET> C-u M-| tidy -q -xml -i -utf8 -

  http://tidy.sourceforge.net
                Home page.
  http://www.emacswiki.org/cgi-bin/wiki/tidy.el
                Emacs bindings.

xmllint.
--------
::

  $ xmllint --format file.xml

or in Emacs:

  : C-x h C-u M-| xmllint --format - <RET>

Emacs and nxml.
---------------

You need introduce line-breaks and then::

  C-x h C-M-\

xmlindent.
----------

  http://xmlindent.sourceforge.net/

c/c++/java/c#.
==============

Artistic Style, astyle.
-----------------------

A Free, Fast and Small Automatic Formatter for C, C++, C#, and Java Source Code.

There are exist package for Cygwin, Debian.

  http://astyle.sourceforge.net/
                home page

Uncrustify.
-----------

Source Code Beautifier for C, C++, C#, ObjectiveC, D, Java, Pawn and VALA.

Exist package for Windows (binary from home page), Debian.

  http://uncrustify.sourceforge.net/
                home page

jpplib.
-------

Pretty Printer Library.

  http://jpplib.sourceforge.net/
                Home page.

Perl.
=====

  http://perltidy.sourceforge.net/
                Home page.

