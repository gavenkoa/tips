.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==============
 File system.
==============
.. contents::

Make label on FAT32 volume.
===========================

The volume name can be up to 11 characters long::

  $ sudo mlabel -i /dev/<device> ::my-label

or when create FAT32 file system::

  $ sudo mkdosfs -n <vol-name> /dev/<device>

Convert file name coding.
=========================
::

  $ convmv --nosmart -f cp-1251 -t utf-8 -r $dir

How get file time attributes.
=============================

POSIX define 3 file time attributes: atime (access time, only a few OS/fs update
this parameter), ctime (attribute/inode modification time), mtime (modification
time).

To get time you can use 'ls' command but it print time in locale dependent
irregular form::

  $ ls -l file.txt      # last file modification
  $ ls -lc file.txt     # last file status modification
  $ ls -lu file.txt     # last access

GNU coreutils provide more robust 'stst' utility::

  $ stat -c %Y file.txt # last file modification
  $ stat -c %Z file.txt # last file status modification
  $ stat -c %X file.txt # last access

POSIX file name restriction.
============================

Windows file name restriction.
==============================

  http://msdn.microsoft.com/en-us/library/aa365247.aspx
                Naming Files, Paths, and Namespaces

How get UUID and label?
=======================

Include UUID (Universally Unique Identifier) and labels::

  $ ls -l /dev/disk/by-uuid/
  lrwxrwxrwx 1 root root 10 2010-11-01 23:41 46B6-1FD4 -> ../../sdb2
  lrwxrwxrwx 1 root root 10 2010-11-01 23:41 4C30299030298256 -> ../../sda1

  $ ls -l /dev/disk/by-label/
  lrwxrwxrwx 1 root root 10 2010-11-01 23:41 bin -> ../../sda3
  lrwxrwxrwx 1 root root 10 2010-11-01 23:41 inst -> ../../sda2
  lrwxrwxrwx 1 root root 10 2010-11-01 23:41 media -> ../../sdc5

  $ sudo vol_id /dev/dm-2
  ID_FS_USAGE=filesystem
  ID_FS_TYPE=ext3
  ID_FS_VERSION=1.0
  ID_FS_UUID=f7484fc9-75ec-4e46-8539-50b1e371b7ef
  ID_FS_UUID_ENC=f7484fc9-75ec-4e46-8539-50b1e371b7ef
  ID_FS_LABEL=
  ID_FS_LABEL_ENC=
  ID_FS_LABEL_SAFE=

  $ /sbin/blkid     ## from 'e2fsprogs' package
  /dev/sdc2: UUID="46B6-1FD4" TYPE="vfat"
  /dev/sdb2: TYPE="ntfs" UUID="BC48D3FD48D3B47C" LABEL="inst"
  /dev/sda5: UUID="5240AED140AEBB5D" LABEL="music" TYPE="ntfs"
  /dev/sdc1: UUID="81c4444f-0b70-429a-9d97-8c13e8651f5b" TYPE="ext3"
  /dev/sdc3: UUID="KOpHWz-clDR-2MqV-vAkE-cPvY-uZrY-kjYJIb" TYPE="lvm2pv"

  $ udevinfo --query=all --name /dev/sdb    ## from 'udev' package
  P: /block/sdb
  N: sdb
  S: disk/by-id/ata-WDC_WD1600JS-00MHB0_WD-WCANM5835587
  S: disk/by-id/scsi-SATA_WDC_WD1600JS-00_WD-WCANM5835587
  S: disk/by-path/pci-0000:00:08.0-scsi-1:0:0:0
  E: ID_VENDOR=ATA
  E: ID_MODEL=WDC_WD1600JS-00M
  E: ID_REVISION=02.0
  ...

How set UUID and label?
=======================

For ext2/ext3 fs::

  $ sudo tune2fs /dev/hdb1 -U `uuid`

Linux fs under Windows.
=======================

Ext2 IFS.
---------

It provides Windows NT4.0/2000/XP/2003/Vista/2008 with full access to Linux Ext2
volumes (read access and write access). This may be useful if you have installed
both Windows and Linux as a dual boot environment on your computer.

The "Ext2 Installable File System for Windows" software is freeware.

After install use 'ifsdrives.cpl' control panel to modify settings.

  http://www.fs-driver.org/
                home page

Ext2Fsd.
--------

Ext2Fsd is an open source linux ext2/ext3 file system driver for Windows systems
(NT/2K/XP/VISTA, X86/AMD64).

  http://www.ext2fsd.com/
                Home page.
  http://sourceforge.net/projects/ext2fsd/
                Sourceforge home page.


rfstool.
--------

Allows you to access ReiserFS partitions from a Windows 95/98/ME/NT/2000/XP
system. It also allows you to access ReiserFS partitions from Linux. It is a
complete rewrite of the ReiserFS functions needed to list directories, copy
files, and backup metadata.

  http://p-nand-q.com/e/reiserfs.html
                home page
  http://freshmeat.net/projects/rfstool/
                Freshmeat home page.

Summary files size.
===================
::

  $ find . -type f -iname "*.log" -print0 | du --files0-from=- -c -m | tail -n 1 \
      | (read first rest; echo $first)

Mount NTFS in Linux.
====================

Mount in rw mode::

  $ man 8 ntfs-3g
  $ cat /etc/fstab
  ...
  UUID=D474CB9874CB7C2C /mnt/winbin ntfs-3g rw,default_permissions,gid=1000,fmask=113,dmask=002,noatime,silent 0 0
  ...

Stop fsck running every 27 boots.
=================================

Check current settings::

  $ tune2fs -l /dev/$DISK

and tune them::

  $ tune2fs -c 0 /dev/$DISK
  $ tune2fs -i 2w /dev/$DISK

Or disable checks in ``/etc/fstab`` completely (by setting last colon to ``0``
value)!