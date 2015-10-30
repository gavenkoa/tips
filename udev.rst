.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 udev.
=======
.. contents::

About.
======

 * http://reactivated.net/writing_udev_rules.html
 * http://wiki.debian.org/udev
 * https://wiki.archlinux.org/index.php/Udev
 * http://wiki.gentoo.org/wiki/Udev
 * http://www.crashcourse.ca/wiki/index.php/Udev

Record udev events.
===================

This dump udev events to console::

  $ sudo udevadm monitor

View device capability with udev compatible format.
===================================================

For Debian use::

  $ /sbin/udevadm info --name=/dev/sdc --attribute-walk
  $ udevadm info --attribute-walk --path $(udevadm info --query=path --name=/dev/ttyUSB0)

For other Linux use::

  $ udevinfo -a -p $(udevinfo -q path -n /dev/sdc)

Debugging udev rule.
====================
::

  $ sudo udevadm trigger
  $ sudo udevadm test $(udevadm info -n /dev/$DEV -q path)

