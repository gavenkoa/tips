.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 Font.
=======
.. contents::

Show list of avaliable font under X.
====================================

To view list of clint-side fonts::

  $ fc-list

To view list of monospaced clint-side fonts::

  $ fc-list :spacing=mono

To view list of server-side monospaced fonts::

  $ xlsfonts -fn '*-*-*-*-*-*-*-*-*-*-*-m*'
  $ xlsfonts -fn '*-*-*-*-*-*-*-*-*-*-*-c*'

View how fonts looks like under X.
==================================
::

  $ xfontsel &
  $ gucharmap &

Configure fonts under X.
========================

Read ``man 5 font-config``.

  http://www.freedesktop.org/software/fontconfig/fontconfig-user.html
                Man page about font.conf.
  http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-fonts.html
                FreeBSD manual about font.conf.
  http://wiki.debian.org/Fonts/
                Debian wiki.
  http://en.wikipedia.org/wiki/X_logical_font_description
                X logical font description.

Setup font for emacs.
=====================

If X running by xinit, write to ~/.xinitrc

  xrdb -merge ~/.Xdefaults &

and write to ~/.Xdefaults

  emacs.font: 7x13

Setup font for mc.
==================

Not any font display correctly cyrillic characters - only those which with
ISO 10646. If you in X run MC as::

  $ xterm -fn "-misc-fixed-medium-r-*-*-18-*-*-*-*-*-iso10646-1" -geometry 120x42 -e mc -x

Fonts family.
=============

See

  http://en.wikipedia.org/wiki/Free_software_Unicode_typefaces
                Free typefaces at Wikipedia.
  http://www.openfontlibrary.org
                Open Font Library, a library of free fonts
  http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=FontsInCyberspace&_sc=1
                SIL fonts.

DejaVu.
-------

The DejaVu fonts are a font family based on the Vera Fonts.

  http://dejavu-fonts.org/wiki/index.php?title=Main_Page

For Debian::

  $ sudo apt-get install ttf-dejavu

Core fonts for the Web.
-----------------------

From Microsoft.

  http://corefonts.sourceforge.net
                mirror
  http://en.wikipedia.org/wiki/Core_fonts_for_the_Web
                Wikipedia article.

Liberation.
-----------

GPL font: Liberation Sans, Liberation Serif and Liberation Mono.

As alternative to Arial, Times New Roman, and Courier New.

  https://fedorahosted.org/liberation-fonts
                home page
  http://en.wikipedia.org/wiki/Liberation_fonts
                Wikipedia article.

Linux Libertine.
----------------

Free and open alternatives to commercial fonts like Times Roman.

  http://www.linuxlibertine.org
                home page
  http://en.wikipedia.org/wiki/Linux_Libertine
                Wikipedia article.

SIL (IPA font).
---------------

Charis SIL, Doulos SIL, Gentium.

  http://scripts.sil.org/DoulosSILfont
  http://scripts.sil.org/CharisSILfont
  http://scripts.sil.org/Gentium

For Debian::

  $ sudo apt-get install ttf-sil-doulos
  $ sudo apt-get install ttf-sil-charis
  $ sudo apt-get install ttf-gentium

Junicode.
---------

Have beta status.

  http://en.wikipedia.org/wiki/Junicode

How configure font for X?
=========================

For Debian::

  $ sudo aptitude install fontconfig-config
  $ sudo dpkg-reconfigure fontconfig-config

Font tuning method for screen:  Native
Enable subpixel rendering for screen: Always (или Automatic)
Enable bitmapped fonts by default?: No

Font development.
=================

Font development under Microsoft.
---------------------------------

  http://www.microsoft.com/typography/DevToolsOverview.mspx
                Tools & SDKs from Microsoft
  http://www.microsoft.com/typography/DevArticles.mspx
                Articles from Microsoft

FontForge.
----------

Typeface (font) editor program. BSD licence.

  http://fontforge.sourceforge.net
                home page
  http://en.wikipedia.org/wiki/FontForge
                Wikipedia article.

Best font for reading.
======================

Рубленые (Гротески).
--------------------

Arial, Verdana, Helvetica.

Verdana наиболее читабельный, у Arial слишком буквы слипаются.

TODO

Trebushet MS
AcademyTT

Droid
Georgia
sans-serif
Calibri
Candara

liberation serif

Book Antiqua

Garamond
Bookman

Tahoma

Courier New, Times New Roman, Lucida Sans Unicode

Подчеркнутый, полужирный или курсивный текст.

Serif - это шрифт с засечками, антиква.

