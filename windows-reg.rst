.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=================
 Registry files.
=================
.. contents::

How to add, modify, or delete registry subkeys and values.
==========================================================
::

  cmd# regedit.exe /s path-to.reg

See:

  http://support.microsoft.com/kb/310516
                How to add, modify, or delete registry subkeys and values by
                using a registration entries (.reg) file.

Syntax of .Reg Files.
=====================

A .reg file has the following syntax::

  RegistryEditorVersion
  Blank line
  [RegistryPath1]
  "DataItemName1"="DataType1:DataValue1"
  DataItemName2"="DataType2:DataValue2"
  Blank line
  [RegistryPath2]
  "DataItemName3"="DataType3:DataValue3"

Deleting Registry Keys and Values.
==================================
::

  [-HKEY_LOCAL_MACHINE\Software\Test]

  [HKEY_LOCAL_MACHINE\Software\Test]
  "TestValue"=-

