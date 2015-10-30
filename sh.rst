.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Shell.
========
.. contents::

Quoting.
========

  http://www.mpi-inf.mpg.de/~uwe/lehre/unixffb/quoting-guide.html
                A Guide to Unix Shell Quoting

Portability.
============

  http://code.dogmap.org/lintsh/
                lintsh is a Bourne shell that optionally warns about suspicious
                or nonportable constructs
  http://www.gnu.org/software/autoconf/manual/html_node/Portable-Shell.html
                Portable Shell Programming

Kill processes after timeout.
=============================
::

  $ yes xxx& p1=$! ; yes ===& p2=$! ; sleep 2; kill $p1; kill $p2

