.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============
 Assempler.
============
.. contents::

Decompile binary file.
======================

With GNU Binutils::

  $ objdump -w -d file.o

Convert ELF to binary format.
=============================
::

  $ objcopy -O binary image.elf image.bin

Convert ELF to Intex hex format.
================================
::

  $ avr-objcopy -O ihex image.elf image.ihex

