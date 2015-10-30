.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========================
 VM (virtual machines).
========================
.. contents::

Virtualization projects.
========================

VMware, VirtualBox, QEMU, Bochs, DosBox.

VirtualBox.
===========

About VirtualBox.
-----------------

  http://www.virtualbox.org/wiki/Guest_OSes
                Guest OSes support status for VirtualBox.

Copy and resize VirtualBox disk.
--------------------------------

I have clear copies of several OSes for VirtualBox. When I need new one I copy
and resize them to get desired size.

To copy I make a copy::

  $ vboxmanage clonehd /path/to/Hurd.vdi /path/to/Hurd-new.vdi

determine size::

  $ vboxmanage showhdinfo /path/to/Hurd-new.vdi

  UUID:                 63b87983-3130-4db3-cd8c-6d693dcfd92b
  Accessible:           yes
  Logical size:         2996 MBytes
  Current size on disk: 1660 MBytes
  Type:                 normal (base)
  Storage format:       VDI
  Format variant:       dynamic default
  In use by VMs:        Hurd (UUID: f7591848-2c60-4c7c-3886-b66bdb35e425)
  Location:             /path/to/Hurd-new.vdi

and then apply new size (in MiB)::

  $ vboxmanage modifyhd --resize 35000 /path/to/Hurd-new.vdi

Next I mount ``parted-magic`` and boot to it and use ``gparted`` to extend
existing fs to free space.

VMWare.
=======

VMWare remote graphical client.
===============================
::

  $ vmware-vmrc.exe -h 192.168.1.2 -u user -p passwd "dir/file.vmx"

