.. -*- coding: utf-8 -*-
.. include:: HEADER.rst

========
 Samba.
========
.. contents::

Installing smbfs.
=================

Install smbfs package::

  $ apt-get install smbfs

Create new group::

  $ groupadd smbgrp

Add permitions for user that may used mount point::

  $ useradd me smbgrp
  $ useradd you smbgrp

Make password file::

  $ cat >/etc/.smbpass
  username=<smb-user>
  password=<smb-pass>
  domain=<WORKGROUP>
  ^D

Make mount point::

  $ mkdir /mnt/smb
  $ chgrp smbgrp /mnt/smb
  $ chmod 770 /mnt/smb

Add this line to ``/etc/fstab``::

  XXX correct uid=root,gid=smbgrp,umode=775,fmask=775
  //192.168.xx.xx/share-point  /mnt/smb  smbfs  rw,credentials=/etc/.smbpass,uid=root,gid=smbgrp,umode=775,fmask=775

Recursively getting files.
==========================

You can use ``TAB``completion in ``smbclient``::

  $ mkdir $DEST
  $ cd $DEST
  $ smbclient -U $DOMAIN/$DOMAINUSER //$IP/$SHARE $DOMAINPASSWORD
  smb> prompt
  smb> recurse
  smb> mget directory\
  ...
  smb> quit

Alternative syntax to run ``smbclient``::

  $ smbclient -U $USER //$IP/$SHARE $PASSWORD
  ...

or::

  $ smbclient -U $USER //$IP/$SHARE
  Password:
  ...

Alternative syntax for ``smbclient`` and additional commands::

  mask ""
  recurse ON
  prompt OFF
  cd 'path\to\remote\dir'
  lcd '~/path/to/local/dir'
  mget *

To list all available shares::

  $ smbclient -U $USER -L //$IP

