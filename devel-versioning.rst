.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=================
 Version format.
=================
.. contents::

Feature set versioning.
=======================

Feature set versioning pretend to show how serious changes made according to
feature availability and how compatible these versions.

Marketing versioning.
=====================

Marketing versioning schema used for marketing, advertising, branding purpose.
It is usually inconsistent and can changed over the time.

Examples of marketing version schema:

 * Years.
 * Ancient gods.
 * Star/satellite/galactic names.

Look thread for GDB:

  http://www.cygwin.com/ml/gdb/2007-07/msg00061.html

There discussed:

 * Is it essential to update major version if significant change made for
   licence? Answer: **NO**!

   GPLv3 is a big deal spread out over the whole GNU project, but not a big deal
   for GDB in particular.
 * Is it right follow date version schema regardless major changes? Answer:
   **NO**!

   Many OS distribution encode year in versions but versions does not present
   featureset but package set instead.

Year as version name.
---------------------

If year used as version some people can decide that 2005 is too old and broken
if it used in 2007. So companies release product by leading year number. So in
2007 they release 2008 version.

Version name components.
========================

 * major
 * minor
 * patch (patchlevel), micro
 * rev (revision)
 * build
 * date
 * hotfix, fix

Version components usually combined in such group::

  major.minor.build
  major.minor.date
  major.minor.hotfix
  major.minor.hotfix.build
  major.minor.rev
  major.minor.rev.build
  major.current.age

Its conventional to have at least a major and minor number.

Prefixing version with a "v" seems to be less common.

Version in package/release name.
================================
::

  PACKAGE-MAJ.MIN.FIX.tar.gz   (Common style)
  PACKAGE-MAJ.MIN.FIX.zip
  PACKAGE-MAJ.MIN.FIX-DISTROFIX.tar.gz  (Cygwin style)
  PACKAGE_EPOCH:MAJ.MIN.FIX-DISTROFIX_ARCH.deb (Debian style)

From "Debian Policy Manual"::

  Package names must consist only of lower case letters (`a-z'), digits
  (`0-9'), plus (`+') and minus (`-') signs, and periods (`.').  They
  must be at least two characters long and must start with an
  alphanumeric character.

If you look carefully there are no any ``_`` (underscore) chars!! Also ``-`` is
portable char in file name accoding to POSIX.

Versioning for libraries/modules/components.
============================================

Major version component.
------------------------

Major number change means that fundamental change made in the architecture of
the system the new version is incompatible with the old one, upgrade between
versions is non-trivial, and any dependent of the prior version will require
code changes to upgrade to the new package.

Major number rare changed (this can take a lot of year).

Minor version component.
------------------------

Minor number change means that the new version is backward compatible with the
previous version but has significant enhancements over the previous version
(like new functionality or changed UI).

Functional enhancement releases. Contain new or significantly changed
functionality and/or layout.

New releases are usually only published several times a year or less.

Revision, micro, bugfix version component.
------------------------------------------

Revision number is updated whenever a bugfix or security patche is applied to
the build such that it doesn't bring a compatibility change or introduce newer
features.

Patches are released frequently (sometimes daily).

Milestone markers.
------------------

 * a (alpha) means new development is complete and code checkins are frozen.
   Alpha builds should work well enough to be testable.
 * b (beta) means most severe bugs are fixed and end users can start trying the
   release.
 * rc (release candidate) are believed to meet all of the criteria for release
   and can be installed on test instances of production systems.

Compatibility formula.
----------------------

Assume that app linked with new version of lib. Thus::

  is_compatible_with_old(old, new) {
    if (old.major != new.major) return 0;
    if (old.minor > new.minor) return 0;
    return 1;
  }

Assume that app linked with old version of lib. Thus::

  is_compatible_with_new(old, new) {
    if (old.major != new.major) return 0;
    return 1;
  }

Versioning for products.
========================

Versioning for products differ from versioning for libraries.

Product is a set of conponents that stalled to some versions. Components can be
switches as written for library versioning:

 * Any fix releases interchanged, greater version mean less bug count.
 * Any minor release interchanged with next minor releases.
 * Major release does not interchanged at all, switching from old to new require
   upgrade.

Product update vs upgrade.
--------------------------

Product update involve:

 * Replacing product executable files, resources files.
 * Config files and user data stay unchanged.

Product upgrade involve:

 * Replacing product executable files, resources files.
 * Config files and used data require modification and performed by upgrade
   scripts or manually by user (if this is ever possible).

Build data.
===========

 * Build number.
 * Build date.
 * VCS revision.
 * Branch-tag used.
 * Overnight build (Y/N).
 * QA tested (Y/N).
 * QA test results (Pass/Fail).
 * Location of full build logs.

Stop your VCS hook to update version!
=====================================

Don't update version without human decision.

Why do not do this on success build:

 * You can have several build machine which may concurrently update version.
 * There does not exist tools for easy querying for status of build by its
   number (as ok/fail, build configuration, date, coverage, lint checks status,
   etc).
 * Some part of development team may not have permission for bumping version and
   they must revert some automatically updated files after build.

Why do not do this from pre-/post-commit hooks:

 * Some changes can only partially introduce feature/bugfix.

Version ordering formula.
=========================

Strongly recommend:

 * Numbers are not decimal fractions. They are integers separated by delimiters.
 * Only offically released versions of the program get version numbers.
   Development snapshots don't. Nor do test releases.
 * If the last component is zero, it may be omitted. Do not distinguish version
   X.Y from version X.Y.0.
 * Avoid using anything other than numbers in version numbers.


Debian version ordering formula.
--------------------------------

The version number of a package.  The format is::

  [<epoch>`:']<upstream_version>[`-'<debian_revision>]

The three components here are:

``epoch``
     This is a single (generally small) unsigned integer.  It may be
     omitted, in which case zero is assumed.  If it is omitted then
     the <upstream_version> may not contain any colons.

     It is provided to allow mistakes in the version numbers of older
     versions of a package, and also a package's previous version
     numbering schemes, to be left behind.

``upstream_version``
     This is the main part of the version number.  It is usually the
     version number of the original ("upstream") package from which
     the ``.deb`` file has been made, if this is applicable.  Usually
     this will be in the same format as that specified by the upstream
     author(s); however, it may need to be reformatted to fit into the
     package management system's format and comparison scheme.

     The comparison behavior of the package management system with
     respect to the <upstream_version> is described below.  The
     <upstream_version> portion of the version number is mandatory.

     The <upstream_version> may contain only alphanumerics[1] and the characters
     ``.`` ``+`` ``-`` ``:`` ``~`` (full stop, plus, hyphen, colon, tilde) and
     should start with a digit. If there is no <debian_revision> then hyphens
     are not allowed; if there is no <epoch> then colons are not allowed.

``debian_revision``
     This part of the version number specifies the version of the
     Debian package based on the upstream version.  It may contain
     only alphanumerics and the characters ``+`` ``.`` ``~`` (plus, full
     stop, tilde) and is compared in the same way as the
     <upstream_version> is.

     It is optional; if it isn't present then the <upstream_version>
     may not contain a hyphen.  This format represents the case where
     a piece of software was written specifically to be turned into a
     Debian package, and so there is only one "debianisation" of it
     and therefore no revision indication is required.

     It is conventional to restart the <debian_revision> at ``1`` each
     time the <upstream_version> is increased.

     The package management system will break the version number apart
     at the last hyphen in the string (if there is one) to determine
     the <upstream_version> and <debian_revision>.  The absence of a
     <debian_revision> compares earlier than the presence of one (but
     note that the <debian_revision> is the least significant part of
     the version number).

The <upstream_version> and <debian_revision> parts are compared by the
package management system using the same algorithm:

The strings are compared from left to right.

First the initial part of each string consisting entirely of non-digit
characters is determined.  These two parts (one of which may be empty)
are compared lexically.  If a difference is found it is returned.  The
lexical comparison is a comparison of ASCII values modified so that
all the letters sort earlier than all the non-letters and so that a
tilde sorts before anything, even the end of a part.  For example, the
following parts are in sorted order from earliest to latest: ``~~``,
``~~a``, ``~``, the empty part, ``a``.[2]

Then the initial part of the remainder of each string which consists
entirely of digit characters is determined.  The numerical values of
these two parts are compared, and any difference found is returned as
the result of the comparison.  For these purposes an empty string
(which can only occur at the end of one or both version strings being
compared) counts as zero.

These two steps (comparing and removing initial non-digit strings and
initial digit strings) are repeated until a difference is found or
both strings are exhausted.

Note that the purpose of epochs is to allow us to leave behind
mistakes in version numbering, and to cope with situations where the
version numbering scheme changes.  It is _not_ intended to cope with
version numbers containing strings of letters which the package
management system cannot interpret (such as ``ALPHA`` or ``pre-``), or
with silly orderings (the author of this manual has heard of a package
whose versions went ``1.1``, ``1.2``, ``1.3``, ``1``, ``2.1``, ``2.2``,
``2`` and so forth).

[1]  Alphanumerics are ``A-Za-z0-9`` only.

[2]  One common use of ``~`` is for upstream pre-releases.  For example,
     ``1.0~beta1~svn1245`` sorts earlier than ``1.0~beta1``, which sorts
     earlier than ``1.0``.

Semver version ordering formula.
--------------------------------
::

  if (A.major != B.major) return A.major > B.major;
  if (A.minor != B.minor) return A.minor > B.minor;
  if (A.patch != B.patch) return A.patch > B.patch;
  if (A.special == B.special) return 0;
  if (A.special == "") return 1;
  if (B.special == "") return -1;
  return A.special > B.special;

**NOTE** Accoding to this definition 1.0.1rc1 < 1.0.1rc10 < 1.0.1rc2 which is
non meaningful.

Odd/even numbering.
-------------------

Who use:

  GLib GTK+ Gimp GNOME Kaffe

Forms of compatibility.
=======================

Backward/forward compatibility.
-------------------------------

Backward compatibility for library, file format, protocol means that new version
of program can work with old library, file format, protocol.

Forward compatibility for library, file format, protocol means that old version
of program can work with new library, file format, protocol but without using
any benefits from new versions and more essentially without posibility damage
any user data.

Example of backward compatibility: adding to graphic library new image format
for reading/saving.

Example of forward compatibility: old browser ignore any new (unknown) HTML
tags.

Source/binary compatibility.
----------------------------

Runtime or binary compatibility mean that binary can be swaped with another
version without breaking normal program work.

Compile time or source compatibility mean that supplied header/interfaces allow
successful compiling/linking.

Examples:

 * Change type of argument in method to more generic take source compatibility
   but break binary compatibility.
 * Adding new method to abstract class take binary compatibility but break
   compilation (unimplement method error).

Format or protocol compatibility.
---------------------------------

File format or protocol backward compatibility mean that new program can use old
format or protocol.

In order to do that file format or protocol MUST store or provide some
versioning information. Usually this done by:

 * Separate versioning field in data.
 * New prefix or name in data.
 * List of feature requirements, supported algorighm, etc.

It is essential to make code that detect unknown or possibly new format or
protocol and stop working with them to avoid user data corruption.

It is essential to make file format or protocol extensible. This can be achieved
by:

 * Reserving some possible names/prefixes for future use.
 * Generalising file format or protocol to envelop more cases.

Extracting version from VCS.
============================

Including version in sources.
=============================

Don't use any ``$REVISION`` like keywords (usual practice in CVS, SVN)!

Use sed, awk, M4 or any other preprocessor for non-compiled or non-preprocessed
files (like .lisp, .py, .java files)::

  $ cat my-version.el.in
  (defvar my-major-version @VMAJOR@
    "Major version.")
  (defvar my-major-version @VMAJOR@
    "Major version.")
  (provide 'my-version)

  $ cat Makefile
  %: %.in
      sed -e 's|@VMAJOR@|$(VMAJOR)|' -e 's|@VMINOR@|$(VMINOR)|' <$< >$@

Pass version component to preprocessed file (like .c, .cxx files) through
preprocessor::

  $ cat my-version.c
  int get_major_version() { return VMAJOR; }
  int get_minor_version() { return VMINOR; }

  $ cat Makefile
  %.o: %.c
      $(CC) -DVMAJOR=$(VMAJOR) -DVMINOR=$(VMINOR) -o $@ $<

Reference.
==========

  http://semver.org/
                Semantic Versioning
  http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version
                Debian
  http://www.openbsd.org/faq/ports/specialtopics.html
                OpenBSD
  http://java.sun.com/j2se/versioning_naming.html
                Oracle
  http://www.intel.com/support/graphics/sb/CS-020667.htm
                Intel
  http://wiki.eclipse.org/index.php/Version_Numbering
                Eclipse
  http://apr.apache.org/versioning.html
                Apache
  http://www106.pair.com/rhp/parallel.html
                Conflict resolution
  http://www.rpm.org/wiki/PackagerDocs/Dependencies
                RH
  http://www.rpm.org/max-rpm/s1-rpm-depend-manual-dependencies.html
                RH
  http://fedoraproject.org/wiki/Packaging/NamingGuidelines
                RH
  http://wikis.sun.com/display/IpsBestPractices/Packaging+Best+Practices+-+Versioning
                Oracle
  http://docs.codehaus.org/display/MAVEN/Dependency+Mediation+and+Conflict+Resolution
                Maven
  http://docs.codehaus.org/display/MAVEN/Versioning
                Maven

