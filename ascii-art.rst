.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============
 ASCII art.
============
.. contents::

Make ASCII logo.
================

``figlet``::

  $ sudo apt-get install figlet

  $ figlet "Hello world"
  $ figlet -f slant "Hello world"

With spaces between letters::

  $ figlet -k -f shadow "Hello world"

``sysvbanner``::

  $ sudo apt-get install sysvbanner

  $ banner Hello

``cowsay``::

  $ sudo apt-get install cowsay

  $ cowsay Hello
  $ cowsay -f duck Hello

To get list of available cow picture file::

  $ cowsay -l

