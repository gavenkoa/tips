.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 HTTP.
=======
.. contents::

Command line tools for HTTP protocol.
=====================================

  http://daniel.haxx.se/docs/curl-vs-wget.html
                Comparing curl and wget.

Recursive site download.
========================

``curl`` does not allow recursive site downloading, only ``wget`` can do this::

  $ wget -r -np -nc -e robots=off -p -k http://DOMAIN/PATH

Get server response header.
===========================
::

  $ wget --server-response http://example.com
  $ wget -S http://example.com    # short variant

  $ curl --dump-header - http://example.com
  $ curl -D - http://example.com

View cookies from site.
=======================
::

  $ wget --save-cookies FILE -O -  http://example.com  >/dev/null
  $ curl --cookie-jar FILE -o - http://example.com  >/dev/null
  $ curl -c FILE -o - http://example.com  >/dev/null

Send cookies to site.
=====================
::

  $ wget --load-cookies FILE  http://example.com
  $ curl --cookie $name=$data  http://example.com
  $ curl -b $name=$data  http://example.com

Send specific header line.
==========================
::

  $ wget --header='Accept-Charset: iso-8859-2' --header='Accept-Language: ru' http://example.com
  $ curl --header 'Accept-Charset: iso-8859-2' http://example.com
  $ curl -H 'Accept-Charset: iso-8859-2' http://example.com

Send POST request.
==================

Log in to the server. This can be done only once::

  $ wget --save-cookies cookies.txt --post-data 'user=foo&password=bar' http://server.com/auth.php

Now grab the page or pages we care about::

  $ wget --load-cookies cookies.txt -p http://server.com/interesting/article.php

Web server in Cygwin.
=====================
::

  $ setup -p apache2,lighttpd,dhttp

Compressing HTTP data.
======================

Starting with HTTP/1.1, web clients can indicate support for compression::

  Accept-Encoding: gzip, deflate

Web server notifies the web client of this via the Content-Encoding header in
the response::

  Content-Encoding: gzip

ETags.
======

Server respond::

  HTTP/1.1 200 OK
  Last-Modified: Tue, 12 Dec 2006 03:03:59 GMT
  ETag: "10c24bc-4ab-457e1c1f"
  Content-Length: 12195

Lately client send::

  GET /i/yahoo.gif HTTP/1.1
  Host: us.yimg.com
  If-Modified-Since: Tue, 12 Dec 2006 03:03:59 GMT
  If-None-Match: "10c24bc-4ab-457e1c1f"

and get respond::

  HTTP/1.1 304 Not Modified

