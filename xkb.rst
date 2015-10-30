.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 xkb.
======
.. contents::

List xkb settings.
==================
::

  $ setxkbmap -query
  rules:      evdev
  model:      pc105
  layout:     us,ru
  variant:    ,
  options:    grp:rwin_toggle,grp_led:scroll

Set en/ru layout.
=================

Empty ``-option`` reset xkb settings::

  $ setxkbmap -layout us,ru -option '' -option grp:rwin_toggle,grp_led:scroll

