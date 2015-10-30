.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==============
 Duplication.
==============
.. contents::

Search for duplicate lines.
===========================

  http://en.wikipedia.org/wiki/Duplicate_code
                wiki page
  http://students.cis.uab.edu/tairasr/clones/literature/
                Code Clones Literature

Open source or free licence:

 * http://duplo.sourceforge.net/
 * http://clonedigger.sourceforge.net/
 * http://www.ccfinder.net/ccfinderxos.html

Proprietary or restricted licence:

 * http://www.txl.ca/nicaddownload.html
 * http://www.harukizaemon.com/simian/index.html
 * http://getatomiq.com/
 * http://www.harukizaemon.com/simian/index.html

Search for duplicate files.
===========================

This utilities only search for duplicate files:

  http://duff.sourceforge.net/
                duff home page
  http://freedup.org/
                freedup home page
  http://dupedit.com/
                dupedit home page
  http://rdfind.pauldreik.se/
                Rdfind home page
  http://code.google.com/p/softenido/wiki/FindRepe
                FindRepe home page

fdupes.
=======
::

  $ sudo apt-get install fdupes

See:

  http://code.google.com/p/fdupes/
                fdupes home page
  http://ru.wikipedia.org/wiki/Fdupes
                fdupes wiki page
  http://packages.debian.org/search?keywords=fdupes
                fdupes Debian package

freedups.
---------

Freedups searches through the directories you specify. When it finds two
identical files, it hard links them together. Now the two or more files still
exist in their respective directories, but only one copy of the data is stored
on disk; both directory entries point to the same data blocks.

  http://www.stearns.org/freedups/
                freedups home page

dupmerge.
---------

Dupmerge reads a list of files from standard input (eg., as produced by "find .
-print") and looks for identical files. When it finds two or more identical
files, all but one are unlinked to reclaim the disk space and recreated as hard
links to the remaining copy.

  https://sourceforge.net/projects/dupmerge/
                dupmerge home page

ssdeep.
-------

ssdeep is a program for computing context triggered piecewise hashes (CTPH).
Also called fuzzy hashes, CTPH can match inputs that have homologies. Such
inputs have sequences of identical bytes in the same order, although bytes in
between these sequences may be different in both content and length.

  http://ssdeep.sourceforge.net/
                ssdeep home page

