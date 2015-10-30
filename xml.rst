.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 XML.
======
.. contents::

About XML.
==========

 * http://xmlhack.ru
 * http://microformats.org/wiki/namespaces-considered-harmful

Converting between schema formants.
===================================
::

  $ man trang
  trang [-I rng|rnc|dtd|xml] [-O rng|rnc|dtd|xsd] $input $output

See:

  http://code.google.com/p/xsdtorngconverter/
                That XSLT transformation converts a XSD schema to RelaxNG.

relaxng-mode.
=============

  http://www.pantor.com/download.html
                RNC Emacs Mode (home page)
  http://www.emacswiki.org/emacs/RELAX_NG
                Emacs wili.
  http://www.relaxng.org/compact-tutorial-20030326.html
                relaxng compact syntax tutorial

utilities for processing xml.
=============================

xmlstar.
--------

XMLStarlet is a set of command line utilities (tools) which can be used to transform,
query, validate, and edit XML documents and files using simple set of shell commands in
similar way it is done for plain text files using UNIX grep, sed, awk, diff, patch, join,
etc.

  http://xmlstar.sourceforge.net/overview.php
                home page

Cygwin.
-------
::

  cmd# setup.exe -p libxml2,libxslt

``libxslt`` provide ``xsltproc``, ``libxml2`` provide ``xmlcatalog`` and
``xmllint``.

XPath query from CLI.
---------------------
::

  $ xmllint --xpath $XPATH file.xml

Microformats.
=============

  http://microformats.org/about

XML encoding.
=============

  http://www.ietf.org/rfc/rfc3023.txt
                XML Media Types
  http://www.xml.com/pub/a/2004/07/21/dive.html
                XML on the Web Has Failed

Validation of xml files.
========================
::

  $ jing schema.rng in.xml
  $ xmllint --relaxng schema.rng in.xml

See:

  http://infohost.nmt.edu/tcc/help/xml/lint.html
                xmllint: A validator for XML files
  http://www.cogsci.ed.ac.uk/~richard/rxp.html
                RXP - an XML parser available under the GPL

Validating using the DOCTYPE.
-----------------------------
::

  $ xmllint --valid --noout file.xml

Validating against a specific DTD.
----------------------------------
::

  $ xmllint --noout --dtdvalid URL file.xml

Validating against a Relax NG schema.
-------------------------------------
::

  $ xmllint --noout --relaxng schema.rng file.xml

If your schema is in Compact Format, you can use the trang program to convert
it to RNG format::

  $ trang file.rnc file.rng

Validating against XSchema.
---------------------------
::

  $ xmllint --noout --schema schema.xsd file.xml

