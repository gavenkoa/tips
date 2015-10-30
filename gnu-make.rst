.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 GNU Make.
===========
.. contents::

Make docs.
==========

  http://make.paulandlesley.org/ http://mad-scientist.net/make/
                Paul D. Smith page about make.
  http://make.paulandlesley.org/autodep.html
                Advanced Auto-Dependency Generation
  http://miller.emu.id.au/pmiller/books/rmch/
                "Recursive Make Considered Harmful" home page.
  http://evbergen.home.xs4all.nl/nonrecursive-make.html
                Implementing non-recursive make.
  http://www.electric-cloud.com/resources/mrmake.php
                Ask Mr. Make

How view list of default make definitions.
==========================================

  $ make -p -f /dev/null

GNU Make Standard Library.
==========================

  http://gmsl.sourceforge.net
                home page

GNU Make configuration.
=======================

Put on top of your Makefile:

  # Disable built in pattern rules.
  MAKEFLAGS += -r
  # Disable built in variables.
  MAKEFLAGS += -R
  # Disable built in suffix rules.
  .SUFFIXES:
  # Default target.
  .DEFAULT_GOAL = all

