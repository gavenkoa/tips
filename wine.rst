.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 Wine.
=======
.. contents::

Useful info.
============

  http://wiki.winehq.org/FAQ
    Official FAQ.

Clearing workspace.
===================

Make workspace backup::

  $ wineboot -k
  $ mv ~/.wine ~/.wine-tmp

Create new workspace::

  $ winecfg

Move old programs (may not always work)::

  $ mv ~/.wine-tmp/opt ~/.wine/opt

Installing into separate workspace.
===================================
::

  $ PROFILE=my-program
  $ export WINEPREFIX=~/.wine-$PROFILE
  $ winetricks dotnet20 dotnet40
  $ wine /path/to/installer.exe
  $ wine $WINEPREFIX/Program\ Files/Program/start.exe

Write simple script to run program in your environment::

  #!/bin/sh
  env WINEPREFIX=~/.wine-my ~/.wine-my/

To make 32-bit environment::

  $ WINEARCH=win32 WINEPREFIX=~/.wine-32 winecfg

winetricks.
===========

List of available packages::

  $ winetricks apps list

Instal .Net 2.0/4.0::

  $ winetricks dotnet20 dotnet40

Wine utils.
===========
::

  $ winecfg

  $ wine control
  $ wine regedit
  $ wine uninstaller
  $ wine notepad

  $ winefile

