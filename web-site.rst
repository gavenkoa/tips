.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 Web site.
===========
.. contents::

Speeding up web site loading.
=============================

  http://developer.yahoo.com/performance/rules.html

robots.txt.
===========

To exclude all robots from the entire server::

  User-agent: *
  Disallow: /

To exclude all robots from part of the server::

  User-agent: *
  Disallow: /cgi-bin/
  Disallow: /tmp/
  Disallow: /junk/

To allow a single robot::

  User-agent: Google
  Disallow:

  User-agent: *
  Disallow: /

To allow all robots complete access::

  User-agent: *
  Disallow:

See:

  http://www.robotstxt.org/
                home page
  http://www.robotstxt.org/robotstxt.html
                About /robots.txt
  http://www.robotstxt.org/faq.html
                Frequently Asked Questions
  http://googlewebmastercentral.blogspot.com/2008/06/improving-on-robots-exclusion-protocol.html
                Improving on Robots Exclusion Protocol

Sitemap.
========

Sitemaps protocol allows a webmaster to inform search engines about URLs on a
website that are available for crawling.

  http://www.sitemaps.org/protocol.html
                Sitemap protocol.
  http://en.wikipedia.org/wiki/Sitemaps
                Wikipedia article.

Web document structure useage.
==============================

  http://dev.opera.com/articles/view/mama/
                Metadata Analysis and Mining Application

Validation.
===========

  http://validator.w3.org/

Add search to your site.
========================

  http://www.google.com/support/customsearch/
                Custom Search Help
  http://help.yahoo.com/l/uk/yahoo/search/basics/basics-13.html
                Can I add a Yahoo! Search box to my site?

Check websites for broken links.
================================

  http://linkchecker.sourceforge.net/
                linkchecker home page.
  http://arthurdejong.org/webcheck/
                webcheck home page.
