.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=============
 Subversion.
=============
.. contents::

Where palced config files?
==========================

The per-user configuration area currently contains three files two
configuration files ('config' and 'servers').

  ``/etc/subversion``
    Unix system wide configurations.
  ``$HOME/.subversion``
    Unix per-user configuration area.
  ``%APPDATA%\Subversion``
    Windows per-user configuration area.

Coping repository.
==================

Making local repository copy::

  $ svnadmin create $SVNROOT
  $ svnsync init file://$SVNROOT svn://$REMOTE
  $ svnsync synchronize file://$SVNROOT

Note that you can't relocate working copy to new repository copy becase of::

  $ svn relocate file://$SVNROOT
  svn: E195009: The repository at 'file:///home/user/devel/repo-copy' has uuid 'b064fe9f-b7ba-459e-afdf-3429ad89a318', but the WC has '11827c6b-1af5-4614-8a8b-dda7fb34cd94'

Coping repository from SourceForge to GoogleCode::

  $ svnsync init https://PROJ.googlecode.com/svn https://PROJ.svn.sourceforge.net/svnroot/PROJ
  $ svnsync --username NAME --password PASSWORD \
                sync https://PROJ.googlecode.com/svn https://PROJ.svn.sourceforge.net/svnroot/PROJ

Disable interactive conflict resolution.
========================================

Write in ``$HOME/.subversion/config``::

  [miscellany]
  interactive-conflicts = no

Creating svn repo.
==================
::

  $ mkdir -p /srv/svn
  $ svnadmin create /srv/svn/$repo
  $ svn co file:///srv/svn/$repo $repo
  $ cd /tmp/$repo
  $ mkdir trunk branches features tags
  $ svn add *
  $ svn st      # check all OK
  $ svn ci -m "Init repo."

For multi-project repo do follow::

  $ mkdir -p /srv/svn
  $ svnadmin create /srv/svn/$repo
  $ svn co file:///srv/svn/$repo $repo
  $ cd /tmp/$repo
  $ for proj in $proj1 $proj2; do mkdir $proj/trunk $proj/branches $proj/features $proj/tags; done
  $ svn add *
  $ svn st      # check all OK
  $ svn ci -m "Init repo."

Run local svn server.
=====================
::

  $ svnserve -d --pid-file=svnserve.pid --root=/srv/svn/proj  # default port: 3690
  $ svn ls svn://localhost    # check all OK
  $ kill -l

Undo bad commit.
================
::

  $ emacs FILE
  ...
  $ svn ci -m "Introduce first bug."
  Sending        trunk/FILE
  Transmitting file data .
  Committed revision 7.
  $ emacs FILE
  ...
  $ svn ci -m "Make a lot of good changes."
  ...
  Committed revision 8.
  ...
  $ emacs FILE
  ...
  $ svn ci -m "Introduce second bug."
  ...
  Committed revision 10.
  $ emacs FILE
  ...
  $ svn ci -m "Make a lot of good changes."
  ...

Now you understand that revision 7 and 10 buggy. You decide revert changes::

  $ svn merge -r 7:6 -r 10:9 FILE
  $ svn ci -m "Reverted revision 7 and 10."

For one changeset revert you can use shortly syntax::

  $ svn merge -c -7 -c -10 FILE

Also you can use ranges::

  $ svn merge -r 10:6 FILE

Merge branches.
===============
::

  $ cd trunk
  $ svn mergeinfo --show-revs eligible ^/branches/feature
  $ svn merge ^/branches/feature
  $ svn ci -m 'Integrate feature X.'

Fix EOL style.
==============
::

  $ find . -type f -name '*.java' -exec svn propset svn:eol-style native {} ';'
  $ svn ci -m 'Fix svn:eol-style.'

Note that this actions pollute history. For example every line of file with
CR/LF (created on Windows on file without ``svn:eol-style native``) after this
actions would have new author in ``svn annotate``, and ``svn diff`` will show
all on all change.

