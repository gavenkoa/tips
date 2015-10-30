.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 Git.
======
.. contents::

Setup git.
==========

Debian.
-------

For Etch Degian release use git-core package from backports,
old 1.4 version of git very dumb compared to new version 1.5::

  $ sudo apt-get install git-core

After install setup some options::

  $ git config --global user.name "Oleksandr Gavenko"
  $ git config --global user.mail "gavenkoa@gmail.com"
  $ cat ~/.gitconfig
  [user]
    name = Oleksandr Gavenko
    mail = gavenkoa@gmail.com

Cygwin.
-------

  $ setup.exe -p git

git over proxy.
===============

Only http:// protocol support proxy (not git://)::

  $ export http_proxy="http://username:password@proxy:port/"
  $ git clone http://github.com/$user/$proj.git $proj

You can store proxy settings under repository local config file::

  $ git config http.proxy http://$user:$passwd@$ip:$port

Start your project.
===================

Setup proj space on fs::

  $ mkdir proj
  $ cd proj
  $ git init
  Initialized empty Git repository in /home/user/tmp/proj/.git/
  $ ls -a
  . .. .git

Add file, make changes, commit all::

  $ emacs Makefile
  ... C-x C-c
  $ emacs app.c
  ... C-x C-c
  $ git add Makefile app.c
  $ git status
  # On branch master
  #
  # Initial commit
  #
  # Changes to be committed:
  #   (use "git rm --cached <file>..." to unstage)
  #
  #       new file: Makefile
  #       new file: app.c
  #

or just::

  $ git add .

Commit newlly added file::

  $ git commit
  ... Write message log ...
  Created initial commit 2169263: My first commit massage.
   1 files changed, 4 insertions(+), 0 deletions(-)
   create mode 100644 app.c

Undo tracking added file.
=========================

You do::

  $ git add badfile
  $ git status
  # On branch master
  # Changes to be committed:
  #   (use "git reset HEAD <file>..." to unstage)
  #
  #       new file:   badfile
  #

To stop tracking badfile do::

  $ git rm --cached badfile
  $ git status
  # On branch master
  # Untracked files:
  #   (use "git add <file>..." to include in what will be committed)
  #
  #       file
  nothing added to commit but untracked files present (use "git add" to track)

or::

  $ git reset badfile

Doing changes.
==============
::

  $ printf "clean:\n<TAB>rm $(wildcard *.o)\n" >>Makefile
  $ git diff
  diff --git a/Makefile b/Makefile
  index e84f7e9..cd2438a 100644
  --- a/Makefile
  +++ b/Makefile
  @@ -1,2 +1,5 @@
   all:
          @echo XXX
          exit 1
  +
  +clean:
  +       rm -f *.o
    $ git add Makefile
    $ git commit -m "Added clean target."
  Created commit 11272b9: Added clean target.
   1 files changed, 1 insertions(+), 0 deletions(-)
   create mode 100644 file

or just::

  $ git commit -a -m "Added clean target."

git analog of 'hg incoming'.
============================

git does not directly support such feature. You can emulate it by::

  $ git fetch
  $ git log master..origin/master   # or just '..origin/master'

By previous commands you grab changes from remote server! You can apply them::

  TODO
  $ git merge

git analog of 'hg outgoing'.
============================

git does not directly support such feature. You can emulate it by::

  $ git fetch
  $ git log origin/master..master   # or just 'origin/master..'

git analog of 'hg glog'.
========================
::

  $ git log --all --graph

Add alias::

  [alias]
  glog = log --all --graph

Git analog of 'hg rollback'.
============================

To edit commit message of last commit::

  $ git commit --amend -m "$MSG"

To edit messages of old commits starting from ``$REV``::

  $ git rebase -i $REV

Git analog of 'hg root'.
========================
::

  $ git rev-parse --show-toplevel

Debug git network operation.
============================

Git uses libcurl for network operation::

  $ export GIT_CURL_VERBOSE=1
  $ git ...

Push new repo to remote.
========================
::

  $ mkdir $REPO
  $ cd $REPO
  $ git init
  $ git add .
  $ git commit -m "Initial commit"
  $ git remote add origin https://$USER:$PASS@$HOST/$REPO
  $ git push -u origin master

Show heads in branch.
=====================
::

  $ git show-ref --heads -s

Find most recent tag for revision.
==================================
::

  $ git describe $REV

List tags with dates.
=====================
::

  $ git log --tags --simplify-by-decoration --pretty="format:%ci %d"

Update to date.
===============
::

  $ git checkout 'master@{1979-02-26}'
  $ git checkout 'master@{1979-02-26 18:30:00}'

Using git to work with SVN offline.
===================================

Prepare SVN and git utilities::

  $ sudo apt-get svn git-core git-svn

Making SVN repo::

    $ cd $HOME/tmp
    $ svnadmin create svn-repo
    $ svn co file://$HOME/tmp/svn-repo svn-devel
    $ cd svn-devel
    $ mkdir tags trunk branches
    $ svn add *
  A         branches
  A         tags
  A         trunk
    $ cd trunk/
    $ printf "all:\n  echo XXX\n" >Makefile
    $ printf "int main() {return 0;}" >main.c
    $ svn add *
    $ cd ..
    $ svn st
  A      trunk
  A      trunk/main.c
  A      trunk/Makefile
  A      branches
  A      tags
    $ svn ci -m init
  Adding         branches
  Adding         tags
  Adding         trunk
  Adding         trunk/Makefile
  Adding         trunk/main.c
  Transmitting file data ..
    $ svn cp -m v0.0 file://$HOME/tmp/svn/trunk file://$HOME/tmp/svn/tags/v0.0
    $ svn cp -m v0.1 file://$HOME/tmp/svn/trunk file://$HOME/tmp/svn/branches/v0.1

Moving SVN changset to git repo::

    $ cd $HOME/tmp
    $ git svn init file://$HOME/tmp/svn git-repo
    $ ls -a
  .  ..  .git
    $ git svn fetch
      A   trunk/main.c
      A   trunk/Makefile
  W: +empty_dir: branches
  W: +empty_dir: tags
  r1 = 52ccd9882979dd53ec198dbac108783ec660410f (git-svn)
      A   tags/v0.0/main.c
      A   tags/v0.0/Makefile
  r2 = 8ec8a772bb6f37ace56b3649066dc84e481ed427 (git-svn)
      M   trunk/Makefile
  r3 = 2c169ff409ed504dd6a092b1e302beb3fd94871e (git-svn)
      A   branches/v0.1/main.c
      A   branches/v0.1/Makefile
  r4 = e68d76f4ba6beea4b9059c1884c1f38ce10831a7 (git-svn)
      M   trunk/Makefile
  r5 = cdde63974454b13ac53f2eeb201aa76c49fd875c (git-svn)
  Checked out HEAD:
    file:///home/sasha/tmp/svn r5

or (in old git version)::

  $ git svn clone file://$HOME/tmp/svn git-repo

Making changes in svn::

    $ cd $HOME/tmp/svn-devel/trunk
    $ echo ".PHONY: clean" >>Makefile
    $ svn ci -m "Added clean to phony."
  Sending        trunk/Makefile
  Transmitting file data .
  Committed revision 6.

Making committed in git::

    $ cd $HOME/tmp/git-repo/trunk
    $ echo ".PHONY: all" >>Makefile
    $ echo "int foo(int x) {return x+x;}" >>main.c
    $ git status
  # On branch master
  # Changed but not updated:
  #   (use "git add <file>..." to update what will be committed)
  #
  #       modified:   Makefile
  #       modified:   main.c
  #
  no changes added to commit (use "git add" and/or "git commit -a")
    $ git commit -a -m "Bug fixed."
  Created commit 222d399: Bug fixed.
   2 files changed, 2 insertions(+), 0 deletions(-)

Getting changes from SVN to git::

    $ git svn rebase
      M   trunk/Makefile
  r6 = 8165e9bfb38e9df09a7313d19606ec227629b670 (git-svn)
  First, rewinding head to replay your work on top of it...
  Applying Bug fixed.
  error: patch failed: trunk/Makefile:6
  error: trunk/Makefile: patch does not apply
  Using index info to reconstruct a base tree...
  Falling back to patching base and 3-way merge...
  Auto-merged trunk/Makefile
  CONFLICT (content): Merge conflict in trunk/Makefile
  Failed to merge in the changes.
  Patch failed at 0001.

  When you have resolved this problem run "git rebase --continue".
  If you would prefer to skip this patch, instead run "git rebase --skip".
  To restore the original branch and stop rebasing run "git rebase --abort".

  rebase refs/remotes/git-svn: command returned error: 1
    $ git add Makefile
    $ git rebase --continue
  Applying Bug fixed.

and return all from git to SVN::

    $ git svn dcommit
  Committing to file:///home/sasha/tmp/svn ...
      M   trunk/Makefile
      M   trunk/main.c
  Committed r7
      M   trunk/main.c
      M   trunk/Makefile
  r7 = 68e782c8d06635f2db4dd69b9ca8599f99da22e2 (git-svn)
  No changes between current HEAD and refs/remotes/git-svn
  Resetting to the latest refs/remotes/git-svn

See what going to SVN repo::

    $ cd $HOME/tmp/svn-devel/trunk
    $ svn diff -r BASE:HEAD
  Index: Makefile
  ===================================================================
  --- Makefile    (working copy)
  +++ Makefile    (revision 7)
  @@ -6,4 +6,4 @@
   .o: .c
      $(CC) $(CFLAGS) -c -o $@ $<

  -.PHONY: clean
  +.PHONY: all clean
  Index: main.c
  ===================================================================
  --- main.c  (working copy)
  +++ main.c  (revision 7)
  @@ -2,3 +2,4 @@
   {
       return 0;
   }
  +int foo(int x) {return x+x;}
    $ svn up
  U    Makefile
  U    main.c
  Updated to revision 7.

gitk.
=====

gitk - The git repository browser. See gitk(1).

Installing::

  $ sudo apt-get instal gitk

Using::

  $ cd /path/to/git-repo
  $ gitk

