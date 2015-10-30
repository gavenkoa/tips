.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=========
 Mac OS.
=========
.. contents::

Free open source repositories for Msc OS X.
===========================================

Fink.
-----

Binary distribution for quick and easy installation, as well as a source
distribution for users preferring more flexibility.

Usually it installed in '/sw' hierarchy.

It uses Defian 'dpkg' and 'apt-get'.

  http://www.finkproject.org/
    Home page,
  http://en.wikipedia.org/wiki/Fink
    Wikipedia.

MacPorts.
---------

Simplify task of compiling and installing open-source software on your Mac.

  http://www.macports.org/
    Home page,
  http://en.wikipedia.org/wiki/MacPorts
    Wikipedia.

Installing Mac OS X in emulator.
================================

Mac OS X in VirtualBox.
-----------------------

Requirements:

 * Processor: Any Intel Processor with VT-x (Virtualization Technology) or AMD-V.
 * RAM: Anything above 1 GB, Recommended 2GB or higher.
 * Disk space: 20GB (minimum)
 * Snow Leopard Retail Disc (or ISO).
 * Virtualbox 3.2.8 (official support for MAC OS X target added since 3.2.6)

Create a new Virtual Machine:

 * System Type: MAC OS X, MAC OS X Server
 * Create Disk (20 GB will suffice)
 * System > Motherboard > Enable IO APIC
 * Acceleration > Enable VT-x/AMD-V
 * Storage > IDE Controller – ICH6
 * Attach New CD drive > select image (OSx86 Leopard)

Under Windows 7 edit file
``С:\User\%UserName%\.VirtualBox\%VMNAME%\%VMNAME%.xml``. Search for block
``ExtraData`` and replace/add nested data::

  <ExtraDataItem name="VBoxInternal2/Devices/e1000f/0/Trusted" value="integer:1"/>
  <ExtraDataItem name="VBoxInternal2/EfiBootArgs" value=" "/>
  <!-- 0 - 640x480, 1 - 800x600, 2 - 1024x768, 3 - 1280x1024, 4 - 1440x900 -->
  <ExtraDataItem name="VBoxInternal2/EfiGopMode" value="3"/>
  <ExtraDataItem name="VBoxInternal2/SmcDeviceKey" value="ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"/>
  <ExtraDataItem name="VBoxInternal2/SupportExtHwProfile" value="on"/>

  <ExtraDataItem name="CustomVideoMode1" value="1280x800x32"/>
  <ExtraDataItem name="GUI/LastCloseAction" value="powerOff"/>

 * http://wiki.osx86project.org/wiki/index.php/Vmware
 * http://wiki.osx86project.org/wiki/index.php/Installation_Guides
 * http://wiki.osx86project.org/wiki/index.php/Tips_And_Tricks
 * http://admin.dp.ua/other-any/36.html

