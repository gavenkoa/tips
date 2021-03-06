.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========================
 Debugging in Mac OS X.
========================
.. contents::

dtruss.
=======

  $ dtruss df -h     # run and examine the "df -h" command
  $ dtruss -p 1871   # examine PID 1871
  $ dtruss -n tar    # examine all processes called "tar"

dtrace.
=======
::

  $ man -k dtrace
  $ dapptrace

See:

  http://en.wikipedia.org/wiki/Dtrace
                Wikipedia home page.

ktrace.
=======

Log files generated by ``ktrace`` are viewable in human-readable form using
``kdump``.

Since Mac OS X 10.5 Leopard, ktrace has been replaced by dtrace.

  http://en.wikipedia.org/wiki/Ktrace
                Wikipedia home page.

