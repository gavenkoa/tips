.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===================
 WiFi under linux.
===================
.. contents::

Getting info about WiFi connection.
===================================
::

  $ /sbin/iwconfig
  $ sudo iwlist wlan0 scanning

..

  http://wiki.debian.org/iwconfig
    Debian wiki.
  http://en.wikipedia.org/wiki/Wireless_tools_for_Linux
    Wireless tools for Linux.
  https://wiki.archlinux.org/index.php/Wireless_network_configuration
    WiFi at Arch wiki.

List of devices.
================
::

  $ iw dev
  $ rfkill list all
  $ ip link show

Rfkill caveat.
==============
::

  $ rfkill list
  $ rfkill unblock wifi

Enable Wifi in recovery mode.
=============================
::

  ifconfig wlan0 up
  iwlist wlan0 scan
  iwconfig wlan0 essid $NETWORK key s:$PASS

