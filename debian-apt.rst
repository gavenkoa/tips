.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 Apt.
======
.. contents::

Conf files.
===========

See man sources.list(5), apt.conf(5), apt_preferences(5).

``/etc/apt/sources.list``::

  deb http://ftp.debian.org.ua/debian/ stable main contrib non-free
  deb http://ftp2.debian.org.ua/debian/ testing main contrib non-free
  deb http://ftp2.debian.org.ua/debian/ unstable main contrib non-free
  deb http://ftp.uk.debian.org/debian/ experimental main contrib non-free
  deb http://www.deb-multimedia.org testing main non-free

``/etc/apt/preferences``::

  Package: *
  Pin: release a=stable
  Pin-Priority: 800

  Package: *
  Pin: release a=testing
  Pin-Priority: 900

  Package: *
  Pin: release a=unstable
  Pin-Priority: 700

  Package: *
  Pin: release a=experimental
  Pin-Priority: 600

Debian releases.
================

Workflow::

  experimental → unstable (sid) → testing → stable

Which package from witch release::

  $ aptitude search ~S~i~Astable
  $ aptitude search ~S~i~Atesting
  $ aptitude search ~S~i~Aunstable
  $ aptitude search ~S~i~Aexperimental

 * https://wiki.debian.org/DebianReleases
 * https://wiki.debian.org/DebianOldStable
 * https://wiki.debian.org/DebianStable
 * https://wiki.debian.org/DebianTesting
 * https://wiki.debian.org/DebianUnstable
 * https://wiki.debian.org/DebianExperimental

Setup backport.
===============

Main backports archive located at http://www.backports.org.

To get packeges gpg sign key::

  $ su
  ...
  $ wget -O - http://backports.org/debian/archive.key | apt-key add -
  $ ^D

Write where packeges places::

  $ cat /etc/apt/sources.list
  deb http://www.backports.org/debian/ etch-backports main contrib non-free

Getting new keys for packages.
==============================
::

  $ sudo apt-get update
  ...
  W: There is no public key available for the following key IDs:
  9AA38DCD55BE302B
  W: GPG error: http://http.us.debian.org etch Release: The following signatures
  couldn't be verified because the public key is not available: NO_PUBKEY
  9AA38DCD55BE302B
  ...

  $ gpg --keyserver pgp.mit.edu --recv-key 9AA38DCD55BE302B \
  --keyserver-options http-proxy=http://user:pass@192.168.1.1:3128
  gpg: requesting key 55BE302B from hkp server pgp.mit.edu
  gpg: key 55BE302B: public key "Debian Archive Automatic Signing Key (5.0/lenny) <ftpmaster@debian.org>" imported
  gpg: no ultimately trusted keys found
  gpg: Total number processed: 1
  gpg:               imported: 1  (RSA: 1)

  $ gpg --export 9AA38DCD55BE302B | sudo apt-key add -
  OK

Install build dependency for package.
=====================================
::

  $ apt-get install build-essential    # install dev LIBC and GCC C/C++
  $ sudo apt-get build-dep $package

If all you want is checking what packages are needed to build a given package::

  $ apt-cache showsrc $package

or check 'Build-Depends' attribute in::

  $ apt-cache show $package

Delete config file for removed packages.
========================================

To get list of such packages use one of::

  $ aptitude search ~c
  $ grep-status -n -sPackage -FStatus config-files

To remove them::

  $ aptitude purge ~c

Delete obsolete packages.
=========================

To get list of such packages use::

  $ aptitude search ~o

To remove them::

  $ aptitude purge ~o

To remove packages that were automatically installed to satisfy dependencies and
are now no longer needed::

  $ sudo apt-get autoremove

Clean up packages cache.
========================

Remove everything from ``/var/cache/apt/archives/`` and
``/var/cache/apt/archives/partial/``::

  $ sudo apt-get clean

Removes package files that can no longer be downloaded, and are largely
useless::

  $ sudo apt-get autoclean

Check package files for modification.
=====================================
::

  $ sudo debsums --changed

Search for packages.
====================
::

  $ aptitude search '?tag(works-with::logfile)'

Find nearest mirror.
====================
::

  $ sudo apt-get install netselect-apt
  $ netselect-apt stable
  $ netselect-apt testing
  $ netselect-apt unstable
  $ netselect-apt experimental
  $ netselect-apt sid

Show dependency graph.
======================
::

  $ apt-cache dotty $PKG | dot -Tsvg >$PKG.svg && see $PKG.svg

  $ sudo apt-get install debtree
  $ debtree $PKG | dot -Tsvg >$PKG.svg && see $PKG.svg

  $ sudo apt-get install apt-rdepends
  $ apt-rdepends $PKG
  $ apt-rdepends -r $PKG
  $ apt-rdepends -d $PKG | dot -Tsvg >$PKG.svg && see $PKG.svg
  $ apt-rdepends -d -r $PKG | dot -Tsvg >$PKG.svg && see $PKG.svg

