.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===================
 DJVU file format.
===================
.. contents::

About djvu.
===========

  http://djvu.org/links/
                many useful links

DJVU viewers.
=============

 * DjVuLibre (all OS).
 * WinDjvu (Windows).

DJVU Editors.
=============

 * DjVuLibre (all OS).
 * DjVu Solo (Windows).

DjVuLibre.
----------

 * A full set of utilities to manipulate and assemble DjVu images and documents.
 * A set of decoders to convert DjVu to a number of other formats.
 * A standalone DjVu viewer for Unix under X11 (based on the Qt library).
 * A browser plugin that works with most Unix browsers

  http://djvu.sourceforge.net/

DjVu Solo.
----------

Tool for editing and merge files and documents in DjVu format from LizardTech.
Currently not maintained.

  http://www.djvu.org/resources/

djvu to pdf.
============

djvulibre::

  $ ddjvu -format=tiff book.djvu book.tiff
  $ tiff2pdf -o book.pdf book.tiff

or directly::

  $ ddjvu -format=pdf book.djvu book.pdf

PDF to Djvu.
============

djvulibre.
----------

For 'pdftoppm' install xpdf (both Linux and Cygwin)::

  $ pdftoppm -mono -r 600 -aa yes  $PREFIX.pdf  $PREFIX
  $ for pbm in $PREFIX*.pbm; do  cjb2 -dpi $DPI $pbm $pbm.djvu;  rm -f $pbm;  done

  $ djvm -c $OUTFILE  $PREFIX*.pbm.djvu

pdf2djvu.
---------
::

  $ pdf2djvu file.pdf

  http://code.google.com/p/pdf2djvu/
                home page

JPEG to Djvu.
=============

JPEG to high quolity DjVu (DjVuPhoto encode)::

  $ c44 -dpi $DPI  $FROM.jpg  $TO.djvu

JPEG to low colour DjVu::

  $ cpaldjvu -dpi $DPI -colors $NCOLORS $i $i.djvu

  $ djvm -c $OUTFILE *.djvu    # Many .djvu to single .djvu.

JPEG to bitonal DjVu::

  $ convert  $PAGE.jpeg  $PAGE.pbm
  $ cjb2 -dpi $DPI  $PAGE.pbm  $PAGE.djvu

  $ djvm -c $OUTFILE *.djvu    # Many .djvu to single .djvu.

if you don't like default delev of balck adjust options::

  $ convert -solarize 50% -level 0,50%  $PAGE.jpeg  $PAGE.pbm

or::

  $ convert  $PAGE.jpeg  pgm:- | pgmtopbm -value 0.499 > page.pbm

