.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======================
 cpp (C preprocessor).
=======================
.. contents::

How to see macros expansion?
============================

GCC::

  $ cpp <file>.c

MSVC::

  $ cl /E <file>.c

Under Emacs select region and type ``C-c C-e``.

How to see predefined macros?
=============================

See:

  http://predef.sourceforge.net/
                ``predef`` project on Sourceforge
  http://en.wikipedia.org/wiki/C_preprocessor#Compiler-specific_predefined_macros
                Compiler specific predefined macros
  http://msdn.microsoft.com/en-us/library/b0084kay.aspx
                Predefined Macros

GNU C Compiler::

  $ gcc -dM -E - < /dev/null

HP-UX ansi C compiler::

  $ cc -v EMPTY.c

SCO OpenServer C compiler::

  $ cc -## EMPTY.c

Sun Studio C/C++ compiler::

  $ cc -## EMPTY.c

IBM AIX XL C/C++ compiler::

  $ cc -qshowmacros -E EMPTY.c

For Visual Studio compiler there no any possibility get predefined macros from
command line... But some macros documented:

  _MSC_VER
                Defines the compiler version. Always defined.
  _WIN32
                Defined for applications for Win32. Always defined.


