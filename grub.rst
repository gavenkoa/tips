.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 GRUB.
=======
.. contents::

Resore GRUB 2.
==============

If you boot to same bit-width kernel (32/64) that have installed you can chroot
to main system and recover by your Linux discto commans::

  mount /dev/sdX /mnt
  sudo mount --bind /dev /mnt/dev &&
  sudo mount --bind /dev/pts /mnt/dev/pts &&
  sudo mount --bind /proc /mnt/proc &&
  sudo mount --bind /sys /mnt/sys
  sudo chroot /mnt
  grub-install /dev/sdX
  update-grub

Check that partition with ``/boot`` directory::

  $ mount /dev/sdX /mnt
  $ ls -l /mnt/boot/grub

Setting text mode resolution on boot.
=====================================

vga=mode

Specifies the VGA text mode that should be selected when booting. mode defaults
to the VGA mode setting in the kernel image. The values are not case-sensitive.
They are:

  ask
      Prompts the user for the text mode. Pressing Enter in response to the
      prompt displays a list of the available modes. extended (or ext)
      Selects 80x50 text mode.
  normal
      Selects normal 80x25 text mode.
  number
      Uses the text mode that corresponds to number. A list of available
      modes for your video card can be obtained by booting with vga=ask and
      pressing Enter.

::

  F00 80x25
  F01 80x50
  F02 80x43
  F03 80x28
  F05 80x30
  F06 80x34
  F07 80x60
  F09 132x25
  F0A 132x43
  F0B 132x50
  F0C 132x60
  100 40x25
  154 132x43
  155 132x25
  164 132x60
  165 132x50
  120 132x25
  121 132x43
  122 132x50
  123 132x60

