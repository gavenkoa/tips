.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=====================
 Driver under Linux.
=====================
.. contents::

NVidia video driver.
====================

To install non-free driver with 3D acceleration::

  $ sudo apt-get install nvidia-glx

Basic configuration can de bone through::

  $ nvidia-xconfig

See:

 * http://wiki.debian.org/GraphicsCard#nVidia
 * http://wiki.debian.org/NvidiaGraphicsDrivers

ATI free driver.
================

  http://wiki.debian.org/AtiHowTo
                Debian ATI howto.

ATI/AMD proprietary driver.
===========================

To install driver under Debian run::

  $ sudo apt-get install fglrx-driver

To create simple ``xorg.conf`` file run::

  $ sudo aticonfig --initial --input=/etc/X11/xorg.conf

To check that driver was loaded properly::

  $ fglrxinfo
  display: :0  screen: 0
  OpenGL vendor string: Advanced Micro Devices, Inc.
  OpenGL renderer string: AMD Radeon HD 6900 Series
  OpenGL version string: 4.2.11566 Compatibility Profile Context

Configure performance in Catalyst Control Center::

  $ amdcccle

  http://wiki.debian.org/ATIProprietary
                Debian ATI Proprietary Driver Howto
  https://help.ubuntu.com/community/BinaryDriverHowto/ATI
                Ubuntu AMD Binary Driver Howto

nouveau video driver.
=====================

Nouveau: Accelerated Open Source driver for nVidia cards.

  http://nouveau.freedesktop.org/wiki/
                home page

