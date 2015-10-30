.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 Perl.
=======
.. contents::

Print stack trace in Perl.
==========================
::

  use Devel::StackTrace;
  my $trace = Devel::StackTrace->new;
  print $trace->as_string; # like carp

Print execution trace in Perl.
==============================

``Devel::Trace`` print out each line before it is executed (like ``sh -x``).

