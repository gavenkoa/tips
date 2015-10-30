.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=========
 Cygwin.
=========
.. contents::

Installation.
=============

Run setup.exe. Use output dir like::

  d:\opt\cygwin

Add to your PATH env var exactly before C:\WINDOWS\system32;C:\WINDOWS values::

  set PATH=d:\opt\cygwin\bin;d:\opt\cygwin\usr\local\bin;%PATH%

  REM Set CYGWIN variable to 'nontsec'. That makes sure that permissions
  REM on your windows machine are not updated as a side effect of cygwin
  REM operations.
  set CYGWIN=binary nontsec nodosfilewarning codepage:cp1251 noglob

  set LANG=ru_RU.cp1251

Set HOME env var (where places config file and projects)::

  set HOME=d:\home

Set TMP and TEMP env vars with good path (without spaces, etc.; these vars
already set as used defined, so you need change their values)::

  set TMP=c:\tmp
  set TEMP=c:\tmp

Also you need edit /etc/passwd to point to correct home path.

Cygwin ports.
=============

This project provides Cygwin binary and source packages for a large variety of programs and
libraries, including the GNOME  and KDE desktop environments

  http://cygwin-ports.sourceforge.net/
                newest home of the Cygwin Ports project
  http://sourceware.org/cygwinports/
                home page
  http://cygwinports.blogspot.com
                official blog??

Which Cygwin version you run?
=============================
::

  $ uname -r
  1.7.7(0.230/5/3)
  $ cygcheck -c cygwin
  Cygwin Package Information
  Package              Version        Status
  cygwin               1.7.7-1        OK

Recreate /etc/passwd and /etc/groups.
=====================================
::

  $ mkpasswd -d | grep $yourlogin > /etc/passwd  # if you in Windows domain
  $ mkpasswd -l > /etc/passwd                    # if you in Windows domain

  $ mkgroup -l > /etc/group

Adding mount points.
====================

``/etc/fstab``::

  C:/foo /bar/baz ntfs text,posix=0 0 0
  /var /usr/var none bind

Running X Window.
=================
::

  $ XWin -multiwindow&

or::

  $ XWin -clipboard -silent-dup-error -xkblayout "us,ru" -xkboptions "grp:caps_toggle"&

To start X application you must set 'DISPLAY'::

  $ DISPLAY=:0 xterm&

Working with packages.
======================

Installed package list with versions.
-------------------------------------
::

  $ cygcheck -c -d

List of package files.
----------------------
::

  $ cygcheck -l pkg-name

Search package by containing file (only under installed packages).
------------------------------------------------------------------
::

  $ cygcheck -f full-path-to-file

Search packages by containing path (only under installed packages).
-------------------------------------------------------------------
::

  $ for f in /etc/setup/*.lst.gz; do gzip -c -d $f | grep $WORD  2>&1 >/dev/null && { echo $f; break; } || :; done

Search for package.
-------------------

If you have file name or regex use (need internet connection)::

  $ cygcheck -p REGEX

cygcheck use such link:

  http://cygwin.com/cgi-bin2/package-grep.cgi?grep=REGEX

Cygwin installation info.
=========================
::

  $ uname -a
  $ cygcheck -s -r

Cygwin acronyms.
================

  http://www.cygwin.com/acronyms
                One encounters all sorts of acronyms on the Cygwin mailing lists.

Check dll dependency.
=====================
::

  $ ldd my.dll
  $ ldd my.exe
  $ cygcheck ./my.dll
  $ cygcheck ./my.exe

Cygwin alternatives.
====================

  http://www.suacommunity.com/SUA.aspx
                Subsystem for Unix-based Applications and Services for Unix
