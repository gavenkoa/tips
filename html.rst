.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 HTML.
=======
.. contents::

Disable quirk mode.
===================
::

  <!DOCTYPE HTML>

Page encoding.
==============

Place in HEAD tag (CHARSET is one among of defined by
http://www.iana.org/assignments/character-sets)::

  <meta http-equiv="Content-Type" content="text/html; charset=CHARSET">

or in HTML 5::

  <meta charset="utf-8">

See:

  http://www.w3.org/TR/REC-html40/charset.html#h-5.2.2

Center an object.
=================

To center block-level element::

  <div style="margin-left: auto; margin-right: auto; position: relative; width: 700px;">
    <div>SOME</div>
  </div>

To center inline element::

  <p style="text-align: center;">TEXT</p>

Browser support.
================

  * http://htmlbook.ru/
  * http://www.quirksmode.org/

