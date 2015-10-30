.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=============
 WEB search.
=============
.. contents::

Disable page indexing by search engine.
=======================================

Add to html page in head tag such code::

  <meta name="ROBOTS" content="NOINDEX,NOFOLLOW" />

General purpose search.
=======================

  http://google.com
  http://yandex.com
  http://yahoo.com
  http://bing.com

Mail list search.
=================

  http://www.mail-archive.com/
    Turns your mailing list into a searchable archive.
  http://www.gmane.org/
    USENET gateway/archive service, some lists may have delay in indexing.
  http://markmail.org/
    Free service for searching mailing list archives.

Image by image search.
======================

 * http://images.google.com/
 * http://www.tineye.com/

Image by text search.
=====================

 * http://en.wikipedia.org/wiki/List_of_CBIR_Engines

Dictionary Search.
==================

 * http://www.onelook.com/

Software search.
================

  http://alternativeto.net
                Search for alternatives.

Code search.
============

  http://code.google.com/
                Google Code.
  http://code.ohloh.net/ http://www.koders.com/
                Search for code in released Open Source tarballs. You can select
                license and language.
  http://www.merobase.com/
                Search for file names in Open Source VCS.
  http://snipplr.com/
                Search for code snippets from its service.

Search in blogs.
================

  http://blogsearch.google.com/
                Google search for blog entries.
  http://www.google.com/search?q=EXPR&tbm=blg&output=atom
                Atom feed for new result of search in blogs.
  http://www.technorati.com/
                Very irrelevant or zero result.

Search for subtitles.
=====================

 * http://www.mysubtitles.com/subtitles

History of word/phrase occurrence.
==================================

  http://www.google.com/trends/
                How often something searched through Google.
  http://books.google.com/ngrams
                Search of phrases in books from 1800 till now day.

DuckDuckGo.
===========

General search engine.

  http://duckduckgo.com/
                search page

Google historical corpus statistics.
====================================

  http://ngrams.googlelabs.com/

Google search query syntax.
===========================

  http://support.google.com/mail/bin/answer.py?answer=7190
                Using advanced search.
  http://www.google.com/support/websearch/bin/answer.py?answer=136861
                Google search basics: More search help
  http://www.google.ru/help/operators.html
                Advanced Operators
  http://code.google.com/intl/ru/apis/soapsearch/reference.html
                Google SOAP Search API Reference
  http://www.google.com/cse/docs/resultsxml.html
                Google WebSearch Protocol Reference for Google Site Search
  http://en.wikipedia.org/wiki/Google_Search
                Google Search

Phrase Search.
--------------

Use double quotes to search exactly mutch of string. Words marked in this way
will appear together in all results exactly as entered::

  "WORD1 WORD2 WORD3"

Note: You may need to use a "+" to force inclusion of common words in a phrase.

Boolean OR Search.
------------------

"OR" capital is essential::

  WORD1 OR WORD2

Remove site from search by "-site:"::

  WORD1 WORD2 -site:ebay.com -site:shopping.com

Include query term (search exactly as is).
------------------------------------------

If a common word is essential to getting the results you want, you can include
it by putting a "+" sign in front of it::

  +WORD WORD1 WORD2

Exclude query term.
-------------------

You can exclude a word from your search by putting a minus sign ("-")
immediately in front of the term you want to exclude from the search results::

  WORD1 WORD2 -WORD

Fill in the blanks.
-------------------
::

  GNU *
  Mozilla *

Site Restricted Search.
-----------------------
::

  site:example.com WORD1 WORD2
  site:.gov WORD

Cached Results Page.
--------------------

The query prefix "cache:" returns the cached HTML version of the specified web
document that the Google search crawled. Note there can be no space between
"cache:" and the web page URL. If you include other words in the query, Google
will highlight those words within the cached document::

  cache:www.google.com

Use Google as a free proxy (if direct access bloked): cache:example.com

Title Search.
-------------

Restricts the results to those with all of the query words in the title::

  intitle:WORD1 intitle:WORD2 WORD3
  allintitle:WORD1 WORD2

Note: Putting "intitle:" in front of every word in your query is equivalent to
putting "allintitle:" at the front of your query.

URL Search.
-----------

If you prepend "inurl:" to a query term, Google search restricts the results to
documents containing that word in the result URL. Note there can be no space
between the "inurl:" and the following word.

Starting a query with the term "allinlinks:" restricts the results to those with
all of the query words in the URL links on the page::

  inurl:WORD1 inurl:WORD2 WORD
  allinurl: WORD1 WORD2

Note: "inurl:" works only on words, not URL components. In particular, it
ignores punctuation and uses only the first word following the "inurl:"
operator. To find multiple words in a result URL, use the "inurl:" operator for
each word.

Note: Putting "inurl:" in front of every word in your query is equivalent to
putting "allinurl:" at the front of your query.

Link anchor search.
-------------------

Searches for text in a page's link anchors. A link anchor is the descriptive
text of a link::

  inanchor:"WORD1 WORD2"

Limit date range.
-----------------
::

  after:2010-01-01  before:2012-01-01

Text Only Search.
-----------------

Starting a query with the term "allintext:" restricts the results to those with
all of the query words in only the body text, ignoring link, URL, and title
matches::

  intext:WORD
  allintext: WORD1 WORD2

File Type Filtering.
--------------------

The query prefix "filetype:" filters the results returned to include only
documents with the extension specified immediately after. Note there can be no
space between "filetype:&quot; and the specified extension::

  WORD filetype:doc OR filetype:pdf

File Type Exclusion.
--------------------

The query prefix "-filetype:" filters the results to exclude documents with the
extension specified immediately after. Note there can be no space between
"-filetype:" and the specified extension::

  WORD -filetype:doc -filetype:pdf

Web Document Info.
------------------

The query prefix "info:" returns a single result for the specified URL if it
exists in the index::

  info:www.google.com

Note: No other query terms can be specified when using this special query term.

Back Links.
-----------

The query prefix "link:" lists web pages that have links to the specified web
page::

  link:www.google.com

Note: there can be no space between "link:" and the web page URL.

Note: No other query terms can be specified when using this special query term.

Related Links.
--------------

Lists web pages that are similar to the specified web page::

  related:www.google.com

Note: there can be no space between "related:" and the web page URL.

Note: No other query terms can be specified when using this special query term.

Word definition.
----------------

The query prefix "define:" will provide a definition of the words listed after
it::

  define:WORD

Yahoo search query syntax.
==========================

  http://help.yahoo.com/l/uk/yahoo/search/basics/index.html
                Yahoo! Search Help Topics
  http://help.yahoo.com/l/uk/yahoo/search/basics/basics-04.html
                Search Tips
  http://help.yahoo.com/l/uk/yahoo/search/basics/basics-08.html
                What is Advanced Search?
  http://help.yahoo.com/l/uk/yahoo/search/basics/basics-19.html
                How do I search for a specific URL, sub-page, or find sites that link to mine?

All of these words.
-------------------

Includes all of the words you typed in the search box. This is similar to
inserting "AND" between words or the symbol "+" before a word.

At least one of these words.
----------------------------

Searches for results that match either one or more of the words. This is similar
to inserting "OR" between the words.

Exact phrase.
-------------

Searches for the words in exactly the order you enter them. This is similar to
putting quotes (" ") around a set of words.

None of these words.
--------------------

Excludes words from your search. This is similar to inserting "NOT" between the
words or the symbol "-" before a word.

site:
-----

This allows one to find all documents within a particular domain and all its
subdomains.

To exclude DOMAIN from search::

  -site:DOMAIN

hostname:
---------

This allows one to find all documents from a particular host only.

link:
-----

This allows one to find documents that link to a particular URL.

url:
----

This allows one to find a specific document in our index.

inurl:
------

This allows one to find a specific keyword as part of indexed URLs.

intitle:
--------

This allows one to find a specific keyword as part of the indexed titles.

Back links.
-----------
::

  linkdomain:DOMAIN

Bing search query syntax.
=========================

  http://onlinehelp.microsoft.com/en-WW/bing/ff808535.aspx
                Bing Help
  http://onlinehelp.microsoft.com/en-us/bing/ff808438.aspx
                Advanced search options
  http://onlinehelp.microsoft.com/en-us/bing/ff524480.aspx
                Search effectively
  http://onlinehelp.microsoft.com/en-us/bing/ff808421.aspx
                Advanced search keywords

"+"
---

Finds webpages that contain all the terms that are preceded by the + symbol.
Also allows you to include terms that are usually ignored.

" "
---

Finds the exact words in a phrase.

"()"
----

Finds or excludes webpages that contain a group of words.

AND or "&".
-----------

Finds webpages that contain all the terms or phrases.

NOT or "-".
-----------

Excludes webpages that contain a term or phrase.

OR or "|".
----------

Finds webpages that contain either of the terms or phrases.

contains:
---------

Keeps results focused on sites that have links to the file types that you
specify::

  contains:wma

filetype:
---------

Returns only webpages created in the file type that you specify::

  filetype:pdf

inanchor: or inbody: or intitle:
--------------------------------

These keywords return webpages that contain the specified term in the metadata,
such as the anchor, body, or title of the site, respectively. Specify only one
term per keyword. You can string multiple keyword entries as needed.

ip:
---

Finds sites that are hosted by a specific IP address. The IP address must be a
dotted quad address. Type the ip: keyword, followed by the IP address of the
website.

language:
---------

Returns webpages for a specific language. Specify the language code directly
after the language: keyword. You can also access this function using the Search
Builder Language function. For more information about using Search Builder, see
Use advanced search.

loc: or location:
-----------------

Returns webpages from a specific country or region. Specify the country or
region code directly after the loc: keyword. To focus on two or more languages,
use a logical OR to group the languages::

  WORD1 WORD2 (loc:US OR loc:GB)

prefer:
-------

Adds emphasis to a search term or another operator to help focus the search
results.

site:
-----

Returns webpages that belong to the specified site. To focus on two or more
domains, use a logical OR to group the domains. You can use site: to search for
web domains, top level domains, and directories that are not more than two
levels deep. You can also search for webpages that contain a specific search
word on a site.

feed:
-----

Finds RSS or Atom feeds on a website for the terms you search for.

hasfeed:
--------

Finds webpages that contain an RSS or Atom feed on a website for the terms you
search for::

  site:www.nytimes.com hasfeed:football

url:
----

Checks whether the listed domain or web address is in the Bing index.

Statistic.
==========

  http://marketshare.hitslink.com/
                Market Share for Mobile and Desktop. Browsers, Operating
                Systems, Search Engines and Social Media Marketing
