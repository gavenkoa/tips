.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Linux.
========
.. contents::

Linux distro.
=============

  http://distrowatch.com/
                Comparing Linux distros.

SysRq.
======
::

  x86: ALT-SysRq-<command key>
  SPARC: ALT-STOP-<command key>
  PPC: ALT - Print Screen (or F13) - <command key>

  'b' - reboot
  'p' - dump the current registers and flags to your console
  'r' - take control of keyboard back from X
  'e' - send SIGTERM to all processes, except for init
  'i' - send SIGKILL to all processes, except for init
  's' - attempt to sync all mounted filesystems
  'u' - remount all filesystems read-only

You can put one of such line::

  $ echo 0 > /proc/sys/kernel/sysrq  # disable
  $ echo 1 > /proc/sys/kernel/sysrq  # enable

to your /etc/rc.local or alternativaly place under /etc/sysctl::

  kernel.sysrq = 1

  http://www.kernel.org/doc/Documentation/sysrq.txt
                Linux Magic System Request Key Hacks

Comunity.
=========

  http://kernelnewbies.org/
    Linux Kernel Newbies

