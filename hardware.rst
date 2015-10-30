.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

================
 List hardware.
================
.. contents::

Linux hardware compatibility databases.
=======================================

  http://www.linux-drivers.org/
    Links for various databases.
  https://h-node.org/
    Hardware database of devices that work with a fully free operating system.
  http://linux-sound.org/hardware.html
    Audio interfaces for Linux.
  http://openbenchmarking.org/
    Public result database from Phoronix Test Suite for Linux.

Distros list of supported hardware:

  https://wiki.debian.org/InstallingDebianOn/
    How to install, configure and use Debian on some specific hardware.
  https://en.opensuse.org/Hardware
    OpenSuse.
  https://hardware.redhat.com/
    RedHat.

List of supported video / graphics card / chipset card by Xorg:

  http://xorg.freedesktop.org/wiki/Projects/Drivers/
    graphics card / chipset

List of supported laptops/mobile::

  http://www.linux-on-laptops.com/
    Reports on running Linux on notebook or laptop computers.
  http://tuxmobil.org/
    Laptop/mobile support.

Printers:

  http://www.openprinting.org/printers
    List of printers.
  http://www.openprinting.org/drivers
    List of drivers.

LAN:

  http://linux-wless.passys.nl/
    Linux wireless LAN support.

List hardware under Linux.
==========================

Command line:

  ``dmesg``
    Messages about detecting new hardware.
  ``lshal -m``
    monitor for hardware changes
  ``lspci``
    All PCI devices.
  ``lspci -vvv``
    All PCI devices. Very verbose output.
  ``sudo lspci -vvvnn``
    All PCI devices. Very verbose output with vendor and device codes as both numbers and names.
  ``hwinfo --short``
    Overview of all hardware, as well as more detailed info.
  ``lshw``
    Another program for listing hardware.
  ``lshw -html | w3m -T text/html``
    Lists hardware with HTML output in the w3m web browser.
  ``uptime``
    Current time elapsed since last reboot, users, and load average.
  ``lsusb``
    USB buses and attached devices.
  ``lsusb -vvv``
    USB buses and attached devices. Very verbose output.

GUI: ``hardinfo``, ``lshw-gtk``.

List hardware under Windows.
============================

  ``%WINDIR%\system32\msinfo32.exe``
    msinfo32
  http://www.cpuid.com/softwares/cpu-z.html
    cpu-z
  ``%WINDIR%\system32\dxdiag.exe``
    DirectX Diagnostic Tool
  ``%WINDIR%\system32\devmgmt.msc /s``
    Device Manager

List processors.
================

  ``cat /proc/cpuinfo``
    All processors, clock speeds, flags, and more.
  ``watch -d grep MHz /proc/cpuinfo``
    CPU MHz speed monitor.
  ``cat /proc/loadavg``
    Processor load average for the last 1, 5, and 15 minutes.
  ``top``
    Press C key to sort processes by CPU usage.
  ``sudo powertop``
    CPU usage by processes, idle/freq/dev stats

List memory.
============

  ``free``
    Total, used, and free memory.
  ``free -m``
    Total, used, and free memory shown in MB.
  ``cat /proc/meminfo``
    Amount of RAM and swap, and how much is being used for what.
  ``top``
    Real-time memory consumption. Press M key to sort processes by memory usage.

::

  $ cat /proc/meminfo
  $ sudo lshw -class memory
  $ sudo lshw -short -C memory
  $ sudo dmidecode --type memory

  $ sudo apt-get install i2c-tools
  $ sudo modprobe eeprom
  $ sudo decode-dimms

  $ read-edid

Graphics card.
==============

  ``glxinfo``
                Details about OpenGL, the Xserver, and your graphics card.
  ``glxinfo | grep direct``
                Do you have direct 3d rendering?
  ``glxinfo | grep vendor``
                Graphics card vendor.
  ``lspci | grep VGA``
                Specific graphics card model.
  ``glxgears``
                A simple 3d benchmark, prints frame rate to the terminal.
  ``xrandr``
                Supported display resolutions.
  ``xdpyinfo``
    Utility for displaying information about an X server.
  ``xvinfo``
    Print out X-Video extension adaptor information.
  ``xdriinfo``
    Query configuration information of DRI drivers.

Audio.
======

  ``lspci | grep Audio``
                Audio controller.
  ``aplay --list-devices``
                More audio device information.

Software versions.
==================

  ``cat /etc/issue``
                Current distribution and version.
  ``apt-cache showpkg packagename``
                Packagename’s version and dependencies.
  ``uname -r``
                Linux kernel version.
  ``uname -a``
                All kernel details.

Networking.
===========

  ``lspci | grep Ethernet``
                Ethernet controllers.
  ``ip addr show``
                List of netword devices, assigned IP addresses and MAC addresses.
  ``ifconfig``
                Networking interfaces, IP addresses, and more.

Hard disks.
===========

  ``df -H``
                Partitions, as well as their mount-points and usage in GB.
  ``sudo fdisk -l``
                All partitions, their device names, and positions on disk.
  ``hwinfo --disk`` or  ``lshw -class disk``
                Disk hardware info.
  ``smartctl``
                Show S.M.A.R.T. reports about disk heals.

Fan/temperature/voltage.
========================

Detect available sensors::

  $ sudo apt-get install lm-sensors
  $ sudo sensors-detect

Load corresponding kernel module, like::

  $ sudo modprobe coretemp

Check output::

  $ sudo sensors

``sensors`` uses ``/sys/class/hwmon/*`` hierarchy.

HDD temperature through SMART::

  $ sudo hddtemp /dev/sd?

BIOS info.
==========

Human readable string with BIOS.motheboard names::

  $ dd if=/dev/mem bs=64k skip=15 count=1 | strings

Find out virtualization type.
=============================
::

  $ sudo apt-get install virt-what
  $ virt-what

  $ sudo apt-get install imvirt
  $ imvirt

