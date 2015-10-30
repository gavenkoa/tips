.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 FVWM.
=======
.. contents::

Obtain FVWM capabilities.
=========================
::

  $ fvwm-config --supports
  $ if fvwm-config --supports-xft; then echo yes; else echo no; fi

  $ fvwm-config --info
  $ fvwm-config --prefix
  $ fvwm-config --bindir
  $ fvwm-config --fvwm-moduledir

Dump Fvwm configuration in runtime.
===================================

Run in Fvwm console::

  PrintInfo style 2
  PrintInfo bindings

and check results in ``~/.xsession-errors``.

Check functions from ``fvwm/functable.c``::

  $ FvwmCommand -i1 send_configinfo
  $ FvwmCommand -i1 send_windowlist
  $ FvwmCommand -i3 send_windowlist

Perl module for FVWM.
=====================
::

  #!/usr/bin/perl -w
  use lib `fvwm-perllib dir`;
  use FVWM::Module;

or::

  use lib `fvwm-config -p | tr -d '0`;
  use FVWM::Module;

FVWM Themes.
============

See

  http://fvwm-themes.sourceforge.net/

FVWM configs.
=============

  http://home.gna.org/fvwm-crystal/features.html
                Usable for ideas how to do things.

Menu.
=====

  https://wiki.archlinux.org/index.php/Xdg-menu
    Generates menus for WMs using the Free Desktop menu standard.

