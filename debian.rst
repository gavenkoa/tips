.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=========
 Debian.
=========
.. contents::

Installing Debian.
==================

 * Download Debian iso CD/DVD image no. 1.
 * Burn it to CD/DVD.
 * Boot from this media.
 * Follow instructions.

Uninstalling unused packages.
=============================
::

  $ sudo apt-get install deborphan
  $ deborphan
  ...
  $ sudo apt-get purge `deborphan`

Also you can use console GUI wrapper around above command::

  $ sudo orphaner

Another tools is cruft (check for cruft in your system)::

  $ sudo apt-get install cruft
  $ cruft

Become sudouser.
----------------
::

  $ su
  ...
  $ emacs /etc/sudoers
  ...
  $ grep -v "^#" /etc/sudoers
  Defaults  env_reset

  root      ALL=(ALL) ALL
  user      ALL=(ALL) ALL
  $ ^D

List existed partitions.
------------------------
::

  $ sudo /sbin/sfdisk -l
  ...

Mount additional partitions.
----------------------------

Partition mounting by hands::

  $ sudo mkdir /mnt/wininst
  $ sudo mount -t ntfs -o ro /dev/sdb2 /mnt/wininst

Automatic partition mounting::

  $ sudo addgroup win
  $ sudo addgroup user win
  $ sudo emacs /etc/fstab
  ...
  $ cat /etc/fstab
  # /etc/fstab: static file system information.
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  /dev/sdc1       /               ext3    defaults,errors=remount-ro 0       1
  /dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
  /dev/sdb1       /mnt/winsys     ntfs    ro,nls=utf8,gid=win,dmask=222,fmask=337  0       0
  /dev/sdb2       /mnt/wininst    ntfs    ro,nls=utf8,gid=win,dmask=222,fmask=337  0       0
  # /dev/sdb3     /mnt/winbin       ntfs-3g rw,utf8,force,gid=win,dmask=002,fmask=113 0    0
  /dev/sdb3       /mnt/winbin     ntfs    rw,utf8,nls=utf8,gid=win,umask=000       0       0
  /dev/sdc2       /mnt/fat        vfat    rw,utf8,gid=win,dmask=222,fmask=337      0       0
  /dev/sda5       /mnt/music      ntfs    ro,nls=utf8,gid=win,dmask=222,fmask=337  0       0
  /dev/sdd1       /mnt/usb        vfat    rw,shortname=winnt,utf8,quiet,gid=win,dmask=002,fmask=111  0  0

Installing and configuring documentation.
=========================================

Documentation packages end with ``-doc`` suffix.

To browse all docs in HTML form install::

  $ sudo apt-get install dhelp info2www man2html swish++

Debian runlevels.
=================

 * 0		System Halt
 * 1		Single user
 * 2		Full multi-user mode (Default)
 * 3-5		Same as 2
 * 6		System Reboot

Show curent runlevel.
=====================
::

  $ /sbin/runlevel

Switching runlevels.
====================
::

  $ sudo telinit 2

