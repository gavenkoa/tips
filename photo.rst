.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Photo.
========
.. contents::

Retrieving media from digital cameras.
======================================
::

  $ sudo apt-get install gphoto2
  $ sudo addgroup camera
  $ sudo adduser user camera
  $ /usr/lib/i386-linux-gnu/libgphoto2/print-camera-list udev-rules mode 0660 group camera | sudo sh -c "cat >/etc/udev/rules.d/90-my-libgphoto2.rules"

You can write own rules::

  $ lsusb | grep Nikon
  Bus 001 Device 005: ID 04b0:031c Nikon Corp.

  $ cat /etc/udev/rules.d/90-my-camera.rules
  ATTRS{idVendor}=="04b0", ATTRS{idProduct}=="031c", MODE="0660", GROUP="camera"

After all those actions restart Linux or restart udev::

  $ sudo service udev restart

and relogin to take ``camera`` group assigned to your user account.

Check if your camera detected::

  $ gphoto2 --auto-detect

List and grab all files::

  $ gphoto2 --list-files
  $ gphoto2 --get-all-files

Install GUI client:

  $ sudo apt-get install gtkam

  https://wiki.archlinux.org/index.php/Libgphoto2
                Digital Cameras



