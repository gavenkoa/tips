.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 NNTP.
=======

Installing INN2 on Debian.
==========================
::

  $ sudo apt-get install inn2
  $ cat /etc/news/inn.conf
  ...
  mta:                    "/usr/sbin/exim4 -oi -oem %s"
  organization:           "My HOME nntp"
  pathhost:               my.org.int
  domain:                 org.int
  maxartsize:             10000
  maxconnections:         10
  ...

  $ cat /etc/news/readers.conf
  ...
  auth bifit {
       hosts: "*.org.int, 192.168.1.0/24"
       default: "<LOCAL>"
  }
  access bifit {
      users: "<LOCAL>"
      newsgroups: "comp.*"
      access: RP
  }
  ...

  $ sudo /etc/init.d/inn2 reload
  $ sudo ctlinnd newgroup comp.general y gavenko@org.int
  $ sudo ctlinnd newgroup comp.general.lang y gavenko@org.int

innd: SERVER cant listen RCreader Address already in use.
---------------------------------------------------------

You need disable IPv6, temporary this done by::

  $ su
  $ echo 1 > /proc/sys/net/ipv6/bindv6only

Public NNTP server.
===================

Gmane.
------

  news:news.gmane.org
                news list address
  http://rss.gmane.org/gmane.<group>.<name>
                rss feed for list
  http://news.gmane.org/gmane.<group>.<name>
                nice web interface for reading list
  http://blog.gmane.org/gmane.<group>.<name>
                make list blog like
  http://search.gmane.org
                search through mailing list

Public NNTP archives.
=====================

  https://groups.google.com/
                Biggest usenet archive.
  http://www.derkeiler.com/
                USENET archive since 2001.
  http://marc.info/
                Very big mailing list archive.
