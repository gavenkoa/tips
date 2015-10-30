.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========================================
 Software configuration management (SCM).
==========================================
.. contents::

About.
======

Configuration management covers the processes used to control, coordinate, and
track: code, requirements, documentation, problems, change requests, designs,
tools/compilers/libraries/patches, changes made to them, and who makes the
changes. (See the 'Tools' section for web resources with listings of
configuration management tools.

Request/issue/bug tracker.
==========================

Each artifact can contain several attributes as:

 * Status.
 * Type.
 * Component.
 * Version.
 * Milestone.
 * Severity.
 * Priority.
 * Resolution.
 * ID.
 * Date.
 * Reposter, assigned, CC.

  http://trac.edgewall.org/wiki/TracTickets
                The Trac Ticket System

Status/State.
-------------

Open/Reopened/Closed.

Type.
-----

Type is a kind of artifact - bug/issue or enhancement or suggestion or wanted,
etc.

Component.
----------

Component is a project module or a subsystem distinct by different criteria.

This can be - client/server, host/target, ui/doc/installer, etc.

Version.
--------

Version vs. build/release number.
---------------------------------

Version is a tag for 

Milestone.
----------

Milestone is a data when issue should be resolved.

Severity.
---------

How danger is bug or issue. For example it may be crash, corruption (of user
data), or misspelling.

Possible values::

  blocker critical major minor trivial

See:

  http://www.debian.org/Bugs/Developer#severities
                Severity levels in Debian project.

Priority.
---------

How important is to fix bug. What bugs are first to fix.

Possible values::

  highest high normal low lowest

Resolution.
-----------

Reason for why a ticket was closed. One of fixed, invalid, wontfix, duplicate.

