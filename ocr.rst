.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 OCS.
======
.. contents::

gocr.
=====

  $ gocr $IN.pnm >$OUT.txt

ocrfeeder.
==========

Document layout analysis and optical character recognition system::

  $ sudo apt-get install ocrfeeder

Using::

  $ ocrfeeder-cli --o $OUTDIR --format HTML --images $IN.pnm

tesseract.
==========

Installing::

  $ sudo apt-get install tesseract-ocr

Using::

  $ tesseract $IN.tif $OUT
  $ cat $OUT.txt

ocropus.
========

  $ ocropus hocr-to-text screen.ppm

ocrad
=====

Optical Character Recognition program::

  $ sudo apt-get install ocrad

Misc.
=====

unpapper
