.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 CVS.
======
.. contents::

CVS via proxy server.
=====================
::

  $ cvs -d:pserver;proxy=$proxyhost;proxyport=$proxyport:$cvsuser@$cvsdomain:/$repo

Create CVS Repository.
======================
::

  $ export CVSROOT=/srv/cvsroot
  $ cvs init

  $ groupadd cvs
  $ useradd -m -g cvs -s /bin/sh -c "CVS Repository"  cvs

  $ chown -R cvs $CVSROOT
  $ chgrp -R cvs $CVSROOT
  $ chmod -R g+s $CVSROOT

  $ grep cvs /etc/services && echo OK
  cvspserver      2401/tcp              # CVS client/server operations
  cvspserver      2401/udp              # CVS client/server operations
  $ echo '# CVS server
  cvspserver  stream  tcp  nowait  root  /usr/bin/cvs cvs --allow-root=/usr/local/src/cvsroot pserver' \
      >/etc/inetd.conf
  $ killall -HUP inetd                  # signal inetd daemon to re-read the config file

  $ ls $CVSROOT/CVSROOT
  readers                   # list of pseudo usernames that can read via cvspserver
  writers                   # list of pseudo usernames can write via cvspserver
  passwd                    # encrypted passwd string with (htpasswd from apache)

CVS workflow.
=============

Check out sources::

  $ cvs co -P $proj

Status of changes::

  $ cvs status

Compare local changes::

  $ cvs diff -u $path

Creating patch::

  $ cvs diff -N -u -r >$patch

History of changes::

  $ cvs log $file

Remove a file::

  $ rm $file            # must first remove it locally
  $ cvs rm $file        # schedules it for removal

Add a file::

  $ cvs add $file

Check in local changes::

  $ cvs ci

Update local sources::

  $ cvs update

Move a file can not be done cleanly at the local level. The best way to do this
with CVS is to go to the cvsroot repository and move the file or directory
within the repository there. The cvsroot repository keeps all files in their RCS
form of filename,v . The next cvs update will manifest the file move.

Tagging sources::

  $ cvs tag $name
  $ cvs rtag $name

Revert file::

  $ rm $file            # remove it from local sources
  $ cvs update $file    # get a new copy from the repository

List of CVS branches.
=====================

There are no such command but this command allow extract such info::

  $ cd $CVS_PROJ
  $ cvs rlog -l -h -b $(cat CVS/Repository)

Update to HEAD.
===============
::

  $ cvs up -A

