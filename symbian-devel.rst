.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=====================================
 Development under Symbian platform.
=====================================
.. contents::

About Symbian platform.
=======================

Supported technologies:

 * Qt with Symbian C++.
 * Symbian C++.
 * Java™ (using MIDP 2.1 with an extensive range of additional JSRs).
 * Web Runtime (WRT) (using standard web technologies).
 * Adobe Flash Lite 4.0.

  http://www.developer.nokia.com/Devices/Symbian/
                Symbian platform

Signing applications.
=====================

Register at https://www.symbiansigned.com/

Register your phone. To get phone IMEI number type in phone::

  *#06#

Download developer's certificate and key, to list it use::

  $ openssl rsa -text -in developercertificate.key
  $ openssl x509 -text -in developercertificate.cer

