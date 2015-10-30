.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========================
 Project branching models.
===========================
.. contents::

Branch types.
=============

Development branch.
-------------------

 * For main development activities.
 * For bug fixes, small enhancements.
 * For development on initial project stage.
 * Does not for experimental features!

Names: dev, devel, master, trunk, default

Feature branch.
---------------

 * For experimental features, that can be striped.
 * For large changes that can break main development.
 * For incompatable changes that can break main development.

Names: feature-xxx

Release branch.
---------------

 * Used to support long running major/minor versions (include bug fixes or
   features backporting).
 * No any new features development.
 * Release branch created from development branch. Decision about branching come
   from release manager after reviewing code quality by QA team.
 * From release branch you make tags to product releases for customer.

Names: vXX.YY.ZZ, maint, stable

Custom branches.
----------------

Custom branches intended to store modification to main release to make custom
product build.

Don't use custom branches at all. Instead redesign project to use customizable
build. Expected problem:

 * You must manually propagate bug fixed to all custom branches.
 * It is not possible merge custom branches back to development branch.

Workflows.
==========

Regular development workflow.
-----------------------------

Regular development stay in development or feature branches.

After completing feature set and testing feature branch merged with top of main
development branch tested again and merged to main development branch.

After completing feature set and testing main development branch merged to
release branch.

Bug fixing workflow.
--------------------

TODO

Single line workflow.
---------------------

 * Only single development branch exist.
 * Release means finish developing set of features and bug fixes on branches and
   moving product build to release server..
 * After testing and stabilising release was made. This means:

   * VERSION file was updated.
   * CHANGE file was filled with feature set, version, data and VCS revision
     number.
   * Mark release by tag in VCS.
   * Invoke build of sources which marked by tag. Copy result to release server.

 * If bug discovered in some version, it fixed at development branch and
   released with new minor/fix product version.
 * Previous major/minor releases do not supported (just use latest release).
   Users always forced to update to latest release.
 * Each new release placed in hierarchy::

     /vendor/product/XX.YY.ZZ/*

   and symlinked to::

     /vendor/product/latest/

Example of release timeline::

  +--+------+------+------+------+------+------+------+------+---->
  dev|      |      |      |      |      |      |      |      |
     v      v      v      v      v      v      v      v      v
    t0.1.0 t1.0.0 t1.0.1 t1.1.0 t1.1.1 t1.1.2 t1.2.0 t2.0.0 t2.1.0

Single development branch with branches for bug fix in major versions.
----------------------------------------------------------------------

 * Each major release have **own** branch.
 * Another single branch reserved for development.
 * Latest major relase branch is active. All older major branches is passive.
 * Passive major branches was used for **only** for minor bug fixes on latest
   code from this major version series (no new features).
 * Features developed in development branch. Before release in merged to active
   major release branch.
 * Bug was fixed in oldest major version branch for which it must be provided
   and merged to all next major version branches and development branch.
 * Release means finish developing set of features and bug fixes on branches and
   moving product build to release server..
 * After testing and stabilising release was made. This means:

   * VERSION file was updated.
   * CHANGE file was filled with feature set, version, data and VCS revision
     number.
   * Mark release by tag in VCS.
   * Invoke build of sources which marked by tag. Copy result to release server.

 * If bug discovered in some version, it fixed at development branch and
   released with new minor/fix product version.
 * Previous major/minor releases do not supported (just use latest release).
   Users always forced to update to latest release.

Example of release timeline::

  +--+-----+----------------------+-----+----+------+------+----->
  dev|     |            ^     ^   |     |    |      |      |
     |     |            |     |   |     |    v      v      v
     |     |            |     |   |     |    +--+------+------+-->
     |     |            |     |   |     |    b2 |      |      |
     |     |            |     |   |     |       v      v      v
     |     |            |     |   |     |      t2.0.0 t2.0.1 t2.1.0
     v     v            |     |   v     v
    t0.1.0 +---+------+-+---+-+-----+------+------+------+------+--->
           b1  |      |     |       |      |      |      |      |
               v      v     v       v      v      v      v      v
              t1.0.0 t1.0.1 t1.0.2 t1.1.0 t1.2.0 t1.2.1 t1.2.2 t1.2.3

In this example we release tags **1.0.1** and **1.0.2** with bug fixes in branch
**1** as development branch was not ready for production.

