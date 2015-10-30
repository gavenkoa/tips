.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 Doxygen.
==========
.. contents::

Installing.
===========
::

  $ sudo apt-get install doxygen
  $ sudo apt-get install doxygen-gui

Graphical wizard called as::

  $ doxywizard

Doxygen simple workflow.
========================
::

  $ cd $proj
  $ doxygen -g $proj.cfg  # generate basic config file

Edit $proj.cfg. Some essential settings::

  PROJECT_NAME     = my-proj
  OUTPUT_DIRECTORY = my
  OUTPUT_LANGUAGE  = English
  INPUT            = my.h my.hpp dir/
  INPUT_ENCODING   = UTF-8
  FILE_PATTERNS    =
  RECURSIVE        = NO
  GENERATE_HTML    = YES

Generate .chm from doxygen.
===========================

Check doxygen config file for::

  GENERATE_HTMLHELP  = YES
  CHM_FILE           = my.chm
  CHM_INDEX_ENCODING = Windows-1251

Run 'doxygen' and 'hhc.exe' on generated 'index.hhp'::

  $ doxygen $proj.cfg
  $ cd $proj/html     # here gone doxygen html output
  $ hhc.exe index.hhp

