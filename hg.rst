.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============
 Mercurial.
============
.. contents::

About.
======

  http://mercurial.selenic.com/wiki/ProjectsUsingMercurial
                Some Projects that Use Mercurial

User config.
============

Put to your ~/.hgrc::

  [ui]
  ; Editor for editing commit message.
  editor = gvim
  ; Who commit.
  username = Oleksandr Gavenko <gavenkoa@gmail.com>
  ; Use internal merge algorithm, which mark conflict like <<<<<< ====== >>>>>>.
  ; Save previous file version in '*.orig' file, after merge must be marked as
  ; resolved by running 'hg resolve -m <file>'.
  merge = internal:merge
  [web]
  ; Default encoding for file hosted by 'hg serv'.
  encoding = utf-8

Multiline log message for log command.
--------------------------------------

By default 'hg log' show only first line of log message. To see all message
run::

  $ hg log -v

or put into ~/.hgrc::

  [defaults]
  log = -v

Follow history ever when file copied.
-------------------------------------

By default 'hg log' show only history after last file copy. To see log message
before copying run::

  $ hg log -f

or put into ~/.hgrc::

  [defaults]
  log = -f

Show supported/loaded plugin.
=============================
::

  $ hg help extensions
  $ hg showconfig extensions

Useful extension.
=================

Put to your ~/.hgrc:

  [extensions]
  ; To allow 'fetch' command.
  hgext.fetch =
  ; To allow Mercurial Queues.
  hgext.mq =
  ; To import revisions from foreign VCS repositories into Mercurial.
  hgext.convert =
  ; Usage:  hg glog <dir>
  hgext.graphlog =
  ; Enable '.hgeol' tracking (fix for CR/LF).
  hgext.eol =

Show diff against 2 parents or base during merge.
=================================================
::

  hg diff -r 'p1()'
  hg diff -r 'p2()'
  hg diff -r 'ancestor(p1(), p2())'

Downgrade repository format.
============================

To get list of supported repo formats type::

  $ hg help config

and look for "format" section. To be Mercurial 0.9.4 compatible use::

  $ hg clone -U --pull \
    --config format.usefncache=0 --config format.dotencode=0 $oldr $newr

Clone specific branches.
========================
::

  $ hg clone http://your/repo -r $branch

Closing branches.
=================
::

  $ hg branches
  $branch (inactive)
  ...
  $ hg branches -a
  ...                     # no $branch
  $ hg up -r $branch
  $ hg ci --close-branch -m "Bla-bla-bla"
  $ hg up -r default
  $ hg branches
  ...                     # no $branch
  $ hg branches -c
  $branch (inactive)
  ...

To reopen closed branch just update to it and commit anything!

Remove/rename files history from repo.
======================================
::

  $ cat >filemap.txt <<EOF
  exclude path/to/file-or-dir
  rename path/to/source path/to/destination
  ...
  EOF
  $ hg convert --filemap filemap.txt $repo_orig $repo_new
  $ hg -R $repo_new up

See:

  http://mercurial.selenic.com/wiki/ConvertExtension

Fix branch names.
-----------------
::

  $ hg convert --branchmap $branchmapfile oldrepo newrepo

To convert non-ASCII names use UTF-8 coding for 'branchmap' file.

When converted names with spaces only last space in 'branchmap' file treat as
separator between old branch name and new, so new branch name can not contain
spaces.

Joining history of two repos.
=============================
::

  $ cat >filemap1.txt <<EOF
  rename . dir1
  EOF
  $ cat >filemap2.txt <<EOF
  rename . dir2
  EOF
  $ hg convert --filemap filemap1.txt $repo1 $repo_new
  $ hg convert --filemap filemap2.txt $repo2 $repo_new
  $ hg -R $repo_new merge
  $ hg -R $repo_new ci -m "Join $repo1 and $repo2."

Publishing repo.
================

With static HTTP hosting you can copy via rsync, ftp, scp, etc., so long as all
the files beneath .hg are copied. Also since 1.1 pull protocol can detect static
HTTP hosting::

  $ hg clone http://example.com/project

See:

  http://mercurial.selenic.com/wiki/hgserve
  http://mercurial.selenic.com/wiki/HgWebDirStepByStep
  http://mercurial.selenic.com/wiki/StaticHTTP

hgweb.config.
-------------

Set allowed project by specifying paths to they (keys are URL, values are fs
paths)::

  [paths]
  myproject = /home/user/hg/myproject
  otherproject = /home/user/hg/otherproject

You can use single wildcard '*' to search current subdirs or double wildcard
'**' to search subdirs recursively::

  [paths]
  myproject = /home/user/hg/my/*
  otherproject = /home/user/hg/other/**

Alternatively you can set a collection of repos (keys and values are both
filesystem paths, keys should be prefixes of the values and are "subtracted"
from the values in order to generate the URL paths to each repository)::

  [collections]
  /home/user/hg = /home/user/hg
  /home/another/hg = /home/another/hg

Allow archive downloads::

  [web]
  allow_archive = gz, zip, bz2

Make web page look nice::

  [web]
  # Use 'cd /lib/python2.x/site-packages/mercurial/templates; find . -type d' to see available
  # styles. Some interesting: gitweb, coal, monoblue.
  style = gitweb

Set another settings::

  [web]
  encoding = UTF-8

  maxchanges = 100
  maxfiles = 100

In each $proj/.hg/hgrc put::

  [web]
  contact = ADMIN <admin@example.com>
  description = <p style="color: red;">$proj</b> allow make a <a href="http://example.com">BIG Thing.</a>
  # Do not use name, in this case you see dir name where project lcated.
  # name = $proj

To allow push in 'hg serv'::

  [web]
  allow_push = *
  push_ssl = false

See:

  http://mercurial.selenic.com/wiki/PublishingRepositories
                Publishing Mercurial Repositories

init.d script.
--------------
::

  #!/bin/sh
  CMD=/usr/bin/hg

  PORT=7878
  SRC=/srv/hg
  CONFIG=/srv/hg/hgweb.config
  PIDFILE=/var/run/hg.pid

  case "$1" in
  start)
    echo "Mercurial Server service starting."
    (cd "$SRC"; $CMD serve -d -p $PORT --pid-file "$PIDFILE")
    ;;
  stop)
    if [ -f "$PIDFILE" ]; then
      PID=`cat "$PIDFILE"`
      if [ "$PID" -gt 1 ]; then
        kill -TERM $PID
        echo "Stopping the Mercurial service PID=$PID."
      else
        echo Bad PID for Mercurial -- \"$PID\".
        echo You may remove \"$PIDFILE\" manually.
      fi
    else
      echo No PID file recorded for mercurial.
    fi
    ;;
  *)
    echo "$0 {start|stop}"
    exit 1
    ;;
  esac

See:

  http://mercurial.selenic.com/wiki/hgserve

Manage patches with MQ.
=======================

First enable MQ, add following to your ~/.hgrc::

  [extensions]
  hgext.mq =

Second get unpatched sources and put it to hg repository::

  $ tar zxf proj-x.y.z.tar.gz
  $ mv proj-x.y.z proj
  $ cd proj
  $ hg init
  $ hg ci -m "Added x.y.z version of proj."

Init MQ and take name for first patch::

  $ hg qinit
  $ hg qnew first.patch

Next make changes by editing source and save it to patch::

  $ $EDITOR file.c
  ...
  $ hg diff
  ...
  $ hg qrefresh
  $ hg diff      # <-- have zero diff

You can make second patch by applying existing one::

  $ hg qnew second.patch
  $ patch -p1 <bugfix.patch
  $ hg qrefresh

You can take list of patches (from old to new) and revert or apply patches by
qpop/qpush command::

  $ hg qseries   # <-- what patches have
  first.patch
  second.patch
  $ hg qapplied  # <-- what patches applied
  first.patch
  second.patch
  $ hg qpop
  $ hg qseries
  first.patch
  second.patch
  $ hg qapplied
  first.patch

You can revert or apply all patches by single command::

  $ hg qpop -a
  $ hg qpush -a

You can delete patch from patch list (before that you need de-apply patch)::

  $ hg qpop -a
  $ hg qdelete first.patch

To add new version of source and fix patches for it first de-apply patches,
then pull new changes and try apply patches on top of new sources::

  $ hg qpop -a
  $ rm *       # .hg dir not deleted because its name start with dot
  $ cd ..
  $ tar zxf proj-a.b.c.tar.gz
  $ cp -R proj-a.b.c/* proj
  $ cd proj
  $ hg addremove -s 70
  $ hg ci -m "Added a.b.c version of proj."
  $ hg qpush -a

To apply series of already done patches use::

  $ ls /path/to/bugfixes/*.patch | xargs hg qimport

You can fix patch description message from command line::

  $ hg qser -s
  makefile-doc.patch:
  $ hg qpush
  applying makefile-doc.patch
  now at: makefile-doc.patch
  $ hg qref -m 'Add description about Makefile usage.'
  $ hg qser -s
  makefile-doc.patch: Add description about Makefile usage.

or from editor by::

  $ hg qref -e

Remove all patches from MQ.
===========================
::

  $ hg qpop -a
  $ for patch in `hg qser`; do hg qrm $patch; done

Moving changes from MQ to working tree.
=======================================
::

  $ hg qpop my.patch
  $ hg qdel --keep my.patch
  $ patch -p1 .hg/patches/my.patch
  $ rm .hg/patches/my.patch

Split patch in MQ.
==================

Enable built-in extensions::

  [extensions]
  mq=
  record=
  shelve=

Then move MQ into working tree and split changes and remove original patch::

  $ hg qpop my.patch
  $ patch -p1 <.hg/patches/my.patch

  $ hg qnew -i my1.patch
   ....
  $ hg qnew -i my2.patch
   ....
  $ hg qnew myN.patch   # last without interactive stuff

  $ hg qdelete --keep my.patch

Between ``my$i.patch`` and ``my$((i+1)).patch`` you can use ``hg shelve``/``hg
unshelve`` to test if project built and pass tests on top of ``my$i.patch``
without later changes!

If you find that something missing on this stage use ``hg qref`` on shelved
changes or ``hg qref -i`` on unshelved changes!

Proxy.
======
::

  $ hg clone --config http_proxy.host=$host:$port \
    --config http_proxy.user=$user --config http_proxy.passwd=$password  $addr

Shelve/stash uncommitted changes.
=================================

Enable ``shelve`` extension::

  [extensions]
  shelve=

and::

  $ hg shelve
  $ hg fetch
  $ hg unshelve

Or use MQ::

  $ hg qnew tmp.patch
  $ hg qpop
  $ hg fetch
  $ hg qpush

Or with plain patch::

  $ hg diff > .diff   # save local changes
  $ hg revert -a
  $ hg fetch
  $ patch -p1 <.diff

See:

  http://mercurial.selenic.com/wiki/TipsAndTricks#Merge_or_rebase_with_uncommitted_changes
  http://mercurial.selenic.com/wiki/ShelveExtension

Rebase.
=======

SVN like update::

  $ hg pull --rebase

Rebase draft (unpublished) changes over public changes if one one head::

  $ hg rebase -s 'draft()' -d 'public()'
  $ hg up  # it possible that you isn't on a tip

If you want to limit merge only to current branch::

  $ hg rebase -s 'draft() & branch(.)' -d 'public() & branch(.)'

Find greatest common ancestor of changesets.
============================================
::

  $ hg help revsets
  $ hg log -r "ancestor($rev1,$rev2)"
  $ hg log -r "ancestor($rev1,ancestor($rev2,$rev3))"

Find most recent tag for revision.
==================================
::

  $ hg log -r "sort(tag() and ancestors($REV),-date)"
  $ hg log -r $REV --template "{latesttag}-{latesttagdistance}-{node|short}\n"

Hooks.
======

Check for bad branch names.
---------------------------

.hg/hgcheck.py::

  import re
  goodbranch_re = r'((bug|feature)#\d|release-1\.\d\.\d|default)$'
  def precommit_badbranchname(ui, repo, hooktype, **kwargs):
      ui.warn('"%s" hook failed\n' % hooktype)
      for rev in repo:
          branch = repo[rev].branch()
          re_ = re.compile(goodbranch_re)
          if not re_.match(branch):
              ui.warn('Invalid branch name "%s".\nUse one of default, bug#ID, feature#ID or release-1.XX.XX.\n' % branch)
              return True
      return False

.hg/hgrc::

  [hooks]
  precommit.badbranchname = python:.hg/hgcheck.py:precommit_badbranchname
  # precommit.gg = python:my.hgcheck.py.precommit_badbranch
  prechangegroup.badbranchname = python:.hg/hgcheck.py:precommit_badbranchname

Read more:

  http://mercurial.selenic.com/wiki/HookExamples

Ignore patterns.
----------------
::

  $ cat $proj/.hgignore
  syntax: glob
  *.o
  .obj
  *.exe

Free Mercurial hosting.
=======================

  http://mercurial.selenic.com/wiki/MercurialHosting
                Free Hosting of Mercurial Repositories

