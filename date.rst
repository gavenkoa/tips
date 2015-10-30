.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

================
 Date and time.
================
.. contents::

System timer and system time.
=============================

Windows.
--------

Windows assume that system timer display locale time.

Debian.
-------

UTC=no - system timer display locale time, UTC=yes - UTC time::

  $ cat /etc/default/rcS
  UTC=no
  # or UTC=yes

If system dual boot with Windows you must set ``UTC=no``.

Getting current date/time.
==========================
::

  $ date +"%Y-%m-%d %H:%M:%S"

Setting current date/time.
==========================
::

  $ sudo date --set="2009-02-22 12:12:00" +"%Y-%m-%d %H:%M:%S"

Or set utc time::

  $ sudo date --utc --set="2009-02-22 12:12:00" +"%Y-%m-%d %H:%M:%S"

May be prefer use ntpdate(8) command.

Get timezone.
=============

System wide configuration::

  $ cat /etc/timezone

Get list of supported timezone.
===============================
::

  $ tzselect

Set timezone.
=============
::

  $ sudo tzconfig
  ...

Or using tzselect::

  $ sudo tzselect
  ...

Debian Lenny.
-------------

  $ sudo dpkg-reconfigure tzdata

About timestamp.
================

 * http://en.wikipedia.org/wiki/Timestamp
 * http://en.wikipedia.org/wiki/Unix_time
 * http://en.wikipedia.org/wiki/Leap_second

Get timestamp.
--------------

Current timestamp::

  $ date +%s

Timestamp for specific date/time::

  $ date -d '2010-12-11' +%s
  $ date -d '2010-12-11 23:59:59' +%s

Convert unix timestamp to date.
-------------------------------
::

  $ date -d '1970-01-01 + 1234567890 seconds'

