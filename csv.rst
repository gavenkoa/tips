.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 CSV.
======
.. contents::

DBF to CSV.
===========
::

  $ sudo aptitude install libdbd-xbase-perl
  $ dbf_dump --fs="=" BSPR.DBF > BSPR.csv

Seems that ``dbf_dump`` can't quote fields, so use rare char as separator!

