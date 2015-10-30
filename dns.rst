.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 DNS.
======

List domain names.
==================
::

  $ dig ns dp.gov.ua
  ...
  ;; ANSWER SECTION:
  dp.gov.ua.              3600    IN      NS      ns.giknpc.com.ua.
  ...

  $ dig @ns.giknpc.com.ua dp.gov.ua AXFR
  ...
  dp.gov.ua.              3600    IN      MX      200 relay2.giknpc.com.ua.
  dp.gov.ua.              3600    IN      A       195.64.190.1
  adm.dp.gov.ua.          3600    IN      A       195.64.190.1

How reread config file?
=======================

FreeBSD::

  $ named.reload
