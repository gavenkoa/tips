.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 Terminal.
===========
.. contents::

Spec.
=====

  http://en.wikipedia.org/wiki/C0_and_C1_control_codes
                C0 and C1 control codes
  http://en.wikipedia.org/wiki/ECMA-48
                ANSI escape sequences

Check terminal capabilities.
============================
::

  $ infocmp -1 xterm
        ...
    colors#8,
    bold=\E[1m,
    blink=\E[5m,
        ...
  $ infocmp -1L xterm    # print long name

  $ tput -Txterm colors
  8
  $ tput -Txterm blink
  ^[[5m

Print highlighted word::

  $ h=`tput smso`
  $ n=`tput rmso`
  $ echo ${h}xxx${n}
  xxx

Old hardware terminal.
======================

VT102.
------

VT100 is a video terminal that was made by Digital Equipment Corporation (DEC). It was introduced in
August 1978. Its detailed attributes became the de facto standard for terminal emulators.

The control sequences used by the VT100 family are based on the ANSI X3.64 standard, later ECMA-48
and ISO/IEC 6429.

The VT101 and VT102 were cost-reduced non-expandable follow-on products, with the VT102 including
the AVO and serial printer port options of the VT100.

In 1983, the VT100 was replaced by the more-powerful VT200 series terminals such as the VT220.

  http://en.wikipedia.org/wiki/VT102

VT220.
------

  http://en.wikipedia.org/wiki/VT220

X window pseudo terminal.
=========================

luit.
-----

Luit is a filter that can be run between an arbitrary application and a UTF-8
terminal emulator. It will convert application output from the locale's
encoding into UTF-8, and convert terminal input from UTF-8 into the locale's
encoding.

Example::

  $ luit -encoding 'ISO 8859-1' emacs -nw

Capture terminal session.
=========================

Use *script* utility::

  $ script out.file
  sh# ....
  ^d
  $ cat out.file
  ...

Installing terminal utilities.
==============================

For Cygwin::

  $ setup.exe -p ncurses

