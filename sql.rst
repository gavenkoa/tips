.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 SQL.
======
.. contents::

Joins.
======

  http://www.codinghorror.com/blog/2007/10/a-visual-explanation-of-sql-joins.html
                A Visual Explanation of SQL Joins.

Primary key length.
===================

For ``int`` type (32-bit): ``NUMBER(9)``. For ``long`` type (64-bit):
``NUMBER(18)``.

Oracle allow up to 38 significant digits in ``NUMBER`` and up to 28 digits in
``SEQUENCE``.

  http://docs.oracle.com/cd/B28359_01/server.111/b28318/datatype.htm
                Oracle Data Types
  http://docs.oracle.com/cd/B28359_01/server.111/b28286/statements_6015.htm
                CREATE SEQUENCE.
  http://docs.oracle.com/cd/E19501-01/819-3659/gcmaz/index.html
                Java Type to SQL Type Mappings.
