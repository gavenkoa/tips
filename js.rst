.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=============
 JavaScript.
=============
.. contents ::

HTML.
=====

``<noscript>`` tag used to render HTML if JavaScript disabled in browser.

Including JavaScript in HTML page.
==================================

In ``head``::

  <html>
    <head>
      <script type="text/javascript" src="abc.js"></script>
    </head>
   ...
  <html>

or alternatively just before closing ``body``::

    <script src="abc.js"></script>
  </body>
  <html>

**NOTE** ``type="text/javascript"`` no longer necessary.

Inlining JavaScript in HTML code.
=================================
::

  <html>
    <h1>Hello!<h1/>
    <script language="javascript">
      <!--
      alert("Hello!")
      document.write("sin(10) = " + Math.sin(10))
      //-->
    </script>
  </html>

Reduce js code size.
====================

  http://crockford.com/javascript/jsmin
                The JavaScript Minifier
  http://developer.yahoo.com/yui/compressor/
                YUI Compressor

JavaScript standards.
=====================

  http://www.ecma-international.org/publications/standards/Ecma-262.htm
                ECMAScript Language Specification.
  http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm
                ECMAScript Language Specification.
  http://www.ecma-international.org/publications/standards/Ecma-327.htm
                ECMAScript 3rd Edition Compact Profile
  http://www.ecma-international.org/publications/standards/Ecma-357.htm
                ECMAScript for XML (E4X) Specification.
  http://www.ecma-international.org/publications/standards/Ecma-290.htm
                ECMAScript Components Specification.

JavaScript versions.
====================

JavaScript 1.5 was introduced back in 1999.

  https://developer.mozilla.org/en-US/docs/JavaScript/Reference#JavaScript.2FBrowser_support_history
                List of versions with CHANGES.
  http://en.wikipedia.org/wiki/Javascript#Versions
                List of versions per browser.
  http://en.wikipedia.org/wiki/ECMAScript#Version_correspondence
                List of versions.
  http://kangax.github.io/compat-table/es5/
                ECMAScript 5 compatibility table.
  http://kangax.github.io/compat-table/es6/
                ECMAScript 6 compatibility table.
  http://kangax.github.io/compat-table/es7/
                ECMAScript 7 compatibility table.
  http://caniuse.com/use-strict
                Can I use ECMAScript 5 Strict Mode?

Pretty print from JavaScript.
=============================
::

  console.debug("%o", obj);

Logging in JS.
==============

To Web Developer console (Firefox/Chrome)::

  console.log("str");
  console.info("str is %s", "str");
  console.warn("this is %o", this);
  console.error("int: %i, float: %f, string: %s, object: %o", 2, .333, "str", this);

To see stack-trace use::

  console.trace();
  console.log(new Error().stack); // only FF

XML from JavaScript.
====================

Powerful, standards-compliant JavaScript XML parser that is designed to help web application
designers implement cross platform applications that take advantage of client-side manipulation of
XML data. XML for <SCRIPT> provides a full suite of tools, including:

 * A standards-compliant W3C DOM Level 2 processor
 * An XPath processor
 * A standards-compliant SAX processor
 * A simple (classic) DOM processor
 * Proxies for XML retrieval from any domain
 * Utilities for XML and application development

  http://xmljs.sourceforge.net/
                home page

