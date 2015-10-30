.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 Printers.
===========
.. contents::

CUPS.
=====

What is CUPS?
-------------

See:

 * http://www.cups.org/
 * http://en.wikipedia.org/wiki/Common_Unix_Printing_System

How access to web interface of CUPS?
------------------------------------

Visit:

  http://localhost:631

Installing on GNU/Debian.
-------------------------
::

  $ sudo apt-get cupsys
  $ sudo apt-get cupsys-client

List of printers.
-----------------
::

  $ lpstat -v
  device for HL2070N: lpd://192.168.1.102/binary_p1

What printer default?
---------------------
::

  $ lpstat -d
  system default destination: HL2070N

or more verbose::

  $ lpstat -s
  system default destination: HL2070N
  device for HL2070N: lpd://192.168.1.102/binary_p1

HP printers.
============

Where find driver for HP printers?
----------------------------------

Follow instructions at:

  http://hplipopensource.com

Debian 6.0 contain all necessary packages to Print from LaserJet 1020::

  $ sudo apt-get install foo2zjs hplip

How about LJ 1020?
------------------

This printer is supported by the foo2zjs free software printer driver.

The printer is faster than the LaserJet 1000 and has a USB connection. It has
only 2 MB of RAM and 32 kB of ROM.

The firmware of the printer must be uploaded after turning it on. You can use a
hotplug/udev script which comes with foo2zjs, or do it manually::

  $ cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0

HP 1020 "out of page" error::

  $ cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0
  $ usb_printerid /dev/usb/lp0

Brother printers.
=================

Работают ли принтеры brother под Linux x86_32/x86_64.
-----------------------------------------------------

Да.

Как настроить принтер.
----------------------

Следует:

 * установить поддержку печати в Unix CUPS
 * установить, если потребуеться, драйвер принтера
 * добавить принтер

Мануал производителя находиться по адресу:

  http://solutions.brother.com/linux/en_us/instruction_prn1a.html

GNU/Debian x86_32.
~~~~~~~~~~~~~~~~~~

Инсталируем 2 пакета, полученых с сайта производителя::

  $ sudo dpkg -i brhl2070nlpr-2.0.1-1.i386.deb
  $ sudo dpkg -i cupswrapperHL2070N-2.0.1-2.i386.deb


GNU/Debian x86_64.
~~~~~~~~~~~~~~~~~~

Инсталируем 2 пакета, полученых с сайта производителя (да, игнорируем что они
предназначены для i386)::

  $ sudo dpkg -i --force-all --force-architecture brhl2070nlpr-2.0.1-1.i386.deb
  $ sudo dpkg -i --force-all --force-architecture cupswrapperHL2070N-2.0.1-2.i386.deb

Добавляем принтер (на примере HL 2070NR) в CUPS.
------------------------------------------------

Пакет cupswrapper добавляет принтер, нам осталось его сконфигурировать (при
изменении настроек может затребуеться аутентификация, в качестве user/password
используем root/<root-pass>):

 * на странице http://127.0.0.1:631/ выбираем принтер
 * меню "Modify Printer"
 * меню "LPD/LPR Host or Printer for Device"
 * адрес lpd://192.168.1.102/binary_p1
 * выбрать производителя из списка (Brother)
 * выбрать модель (HL 2070NR не было, выбрал HL 2060N)
 * установить этот принтер по умолчанию - "Set As Default"
 * добавить пользователей, которые имеют право на печать - "Set Allowed User"

Пробуем напечатать пробную страницу.

Virtual printer.
================

PDFCreator.
-----------

Free/GPL virtual printer for Windows.

  http://www.pdfforge.org/
                Home page.
  http://ru.wikipedia.org/wiki/PDFCreator
                Wikipedia page.

