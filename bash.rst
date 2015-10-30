.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 Bash.
=======
.. contents::

How override PS1, PS2?
======================

When loading bash read ~/.bash_profile and ~/.bashrc.

Put at end of these files::

  PS1='\u@\H$ '

When xterm start bash - it start as non-login. So ~/.bash_profile and ~/.bashrc
didn't read. To workaround this use::

  $ xterm -e bash -i -c "mc -x"

That make bash interactive and init file was readed.

Command history.
================

Bash allow accessing to command that you type previously. There are several
options to control command history behavior. Set corresponding variables in
your ~/.bashrc file (which is read by interactive shell)::

  #   ignorespace do not save lines that start with space
  #   erasedups all previous lines matching the current line to be removed from
  #             the history list before that line is saved
  export HISTCONTROL=igrorespace:erasedups
  export HISTIGNORE=" ?cd *":"e *":"sudo mv *":"sudo rm *":"sudo cp *":"sudo mkdir *":"sudo chmod *":"sudo chown *":ls:pwd:"vlc*"

There are another options, with default values (which satisfy my needs, so
I don't put they to ~/.bashrc)::

  export HISTFILE=~/.bash_history  # where is command history stored
  export HISTFILESIZE=500          # how many lines been in $HISTFILE
  export HISTSIZE=500              # how many lines been stored in bash process

mc (GNU Midnight Commander).
----------------------------

You can also set special history rules for mc subshell in ~/.mc/bashrc file.

Bash history.
=============

  http://wiki.bash-hackers.org/scripting/bashchanges
                This article is an incomplete overview of changes to Bash over
                the time.


