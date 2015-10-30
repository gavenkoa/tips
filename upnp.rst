.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============
 UPnP/DLNA.
============
.. contents::

Discover UPnP services.
=======================
::

  $ gssdp-discover -i wlan0 --timeout=3

Mount UPnP.
===========
::

  $ apt-get install djmount
  $ modprobe fuse
  $ djmount -o iocharset=UTF-8,allow_other /media/upnp

UPnP players.
=============

  http://en.wikipedia.org/wiki/List_of_UPnP_AV_media_servers_and_clients

UPnP Android player.
====================

  https://play.google.com/store/apps/details?id=b4a.upnpBrowser
    UPNP Browser. Pure DLNA browser. Bypass playing to another installed
    applications.
