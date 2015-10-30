.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Emacs.
========
.. contents::

About.
======

  http://elpa.gnu.org/
                Packages for Emacs. This requires Emacs version 24.1 or
                higher.

Getting help.
=============

 * http://news.gmane.org/gmane.emacs.help
 * http://news.gmane.org/gmane.emacs.announce
 * http://news.gmane.org/gmane.emacs.auctex.announce

Installing Emacs.
=================


  http://ftp.gnu.org/gnu/emacs/windows/
                Clean GNU Emacs for 32-bit Windows.
  http://alpha.gnu.org/gnu/emacs/windows/
                Official alpha build of GNU Emacs.
  http://emacsformacosx.com/
                Clean GNU Emacs for Mac OS X.

Development.
============

Variables.
----------

Select one of::

  (set 'variable value)
  (setq variable value)
  (defvar variable value "documentation")

or file local::

  # Local variables:
  # variable: value
  # End:

Find variable/function/feature by name or value.
------------------------------------------------
::

  (apropos-value "PATT")
  (apropos-variable "PATT")
  (apropos-function "PATT")
  (apropos-library "PATT")
  (apropos-documentation "PATT")

Debugging.
==========

Evaluating elisp expression on the fly.
---------------------------------------

Type ``M-:`` than lisp expression than type ``RET``.

Or in any buffer place point at the end of lisp expression and type ``C-x C-e``.

Or invoke elisp "shell" by ``M-x ielm``.

What functions and variables Emacs load and from which files?
-------------------------------------------------------------

See value of variable ``load-history`` (by C-h v load-history RET)::

  (symbol-file 'scheme 'provide)        ; Who provide feature.
  (symbol-file 'nxml-mode-hook 'defvar) ; Where variable defined.
  (symbol-file 'message-send 'defun)    ; Where function defined.
  (symbol-file 'scheme)  ; Look for symbol despite its type.
  load-history
  (locate-library "gnus.el")
  (find-lisp-object-file-name 'c-mode (symbol-function 'c-mode))

Using edebug.
-------------

Execute ``M-x edebug-defun`` (also on ``C-u C-M-x``) on defun in source code to
enable debugging for desired function. When next time this function invoked
you entered to its debugging (jumped to its source code).

To start debug execute code which used debugged function.

You can disable edebug on a function by evaluating the function again using
``C-M-x``.

How debug func?
---------------

Use M-x debug-on-entry and M-x cancel-debug-on-entry to control
which functions will enter the debugger when called.

When next time that function called automatically loaded debug-mode.

You can use ``(debug)`` in your function to automatically enter to debugger.

You can use ``(backtrace)`` to print a trace of Lisp function.

How debug ini file?
-------------------

When your ini has a bug, or when you load external files that cause errors, the
bug is often hard to find, because the Emacs Lisp reader does not know about
line numbers and files - it just knows an error happened, and that's it.

Try run Emacs with ``--debug-init`` to see backtrace.

How debug long running command?
-------------------------------

``M-x debug-on-quit RET`` and then just hit ``C-g`` next time it gets ``stuck``
somewhere.

Check if bug in ini file not in Emacs itself.
---------------------------------------------

First run Emacs without loading anything::

  $ emacs --no-init-file --no-site-file

or more shortly (as ``-Q`` imply ``-q``, ``--no-site-file``, and ``--no-splash``
together)::

  $ emacs -Q

If bug not reproduced bug lies in ini files!

Debug by binary search.
-----------------------

Select half of the file in a region, and M-x eval-region. Depending on whether
that causes the error or not, split this half or the other half again, and
repeat.

Simplified Binary Search.
~~~~~~~~~~~~~~~~~~~~~~~~~

Add (error ``No error until here``) in the middle of your file. If you get the
error ``No error until here`` when reloading the file, move the expression
towards the back of the file, otherwise towards the front of the file.

Elisp debug tips.
-----------------

 * Use a keyboard macro that moves forward one expression (sexp) and evaluates
   it.
 * Try C-x check-parens.

Enable debug mode (also on loading).
------------------------------------

Set in source::

  (setq debug-on-error t)

or invoke Emacs like::

  $ emacs --debug-init

where ``--debug-init`` binds ``debug-on-error`` to ``t`` while loading the init
file, and bypasses the ``condition-case`` which normally catches errors in the
init file.

Call tree.
----------

Before byte compiling file execute::

  (setq byte-compile-generate-call-tree t)

Veiw buffer local variables.
----------------------------
::

  (pp (buffer-local-variables))

Emacs profiling.
================

benchmark.el.
-------------
::

  (benchmark-run 1 (revert-buffer))
  (benchmark-run-compiled 1 (hi-lock-face-phrase-buffer "hello" 'hi-yellow))

elp.el.
-------

Enter a prefix for ``M-x elp-instrument-package``, perform action and see result
by ``M-x elp-results``. To perform new measurement don't forget to run
``M-x elp-reset-all``.

WWW.
====

Text based WWW browser.
-----------------------

 * http://en.wikipedia.org/wiki/W3m
 * http://emacs-w3m.namazu.org/
 * http://www.gnu.org/software/w3/

Tricks.
=======

Sort and uniquify lines.
------------------------

Select region, type ``C-u M-| sort -u RET``.

With transient-mark-mode and delete-selection-mode enabled: select region,
type M-| sort -u RET to replace selection with sorted and uniquified lines.

Determining running environment/platform.
=========================================

Check variables::

  emacs-major-version
  emacs-minor-version
  window-system             - ``nil`` if in terminal, ``w32`` if native Windows build, ``x`` if under X Window
  window-system-version     - for windows only
  window-size-fixed
  operating-system-release  - release of the operating system Emacs is running on
  system-configuration      - like configuration triplet: cpu-manufacturer-os
  system-configuration-options
  system-name               - host name of the machine you are running on
  system-time-locale
  system-type               - indicating the type of operating system you are using:
                              ``gnu`` (GNU Hurd),
                              ``gnu/linux``,
                              ``gnu/kfreebsd``, ``berkeley-unix`` for (FreeBSD),
                              ``darwin`` (GNU-Darwin, Mac OS X),
                              ``ms-dos``,
                              ``windows-nt``,
                              ``cygwin``
  system-uses-terminfo
  dynamic-library-alist or deprecated image-library-alist
                            - alist of image types vs external libraries needed to display them

and check functions::

  (fboundp ...)             - return t if SYMBOL's function definition is not void
  (featurep ...)            - returns t if FEATURE is present in this Emacs
  (display-graphic-p)       - return non-nil if DISPLAY is a graphic display; graphical
                              displays are those which are capable of displaying several
                              frames and several different fonts at once
  (display-multi-font-p)    - same as ``display-graphic-p``
  (display-multi-frame-p)   - same as ``display-graphic-p``
  (display-color-p)         - return t if DISPLAY supports color
  (display-images-p)        - return non-nil if DISPLAY can display images
  (display-grayscale-p)     - return non-nil if frames on DISPLAY can display shades of gray
  (display-mouse-p)         - return non-nil if DISPLAY has a mouse available
  (display-popup-menus-p)   - return non-nil if popup menus are supported on DISPLAY
  (display-selections-p)    - return non-nil if DISPLAY supports selections

Run those checks as below::

  (when window-system ...)
  (when (eq window-system 'x) ...)
  (when (>= emacs-major-version 22) ...)
  (when (fboundp '...) ...)
  (when (featurep '...) ...)

Compiling emacs.
================

Windows.
--------

Get MSYS for POSIX shell and utilities . Get MinGW for GCC. Get Gnuwin32 for
jpeg, ungif, tiff, xpm, png, zlib libraries.

Read emacs/nt/INSTALL::

  $ cmd
  $ cd emacs\nt
  $ configure.bat --prefix %INST_ROOT% --with-gcc --cflags -I%GNUWIN32_ROOT%/include --ldflags -L%GNUWIN32_ROOT%/lib  --ldflags -lregex
  $ make bootstrap
  $ make info
  $ make install

Documentation.
==============

Elisp documentation.
--------------------
::

  ;;; <file-name>.el --- <one-line-description>

  ;; Copyright (C) <years> <person>

  ;; Author: <person> <mail>
  ;; Maintainer: <person> <mail>
  ;; Created: <date>
  ;; Version: <version>
  ;; Keywords: <look for ``finder-by-keyword`` output, separate by comma>
  ;; URL: <file-location>

  ;;; Commentary:
  <bla-bla-bla>
  ;;; Code:
  <lisp-code>
  ;;; <file-name> ends here

See

 * http://www.gnu.org/software/emacs/elisp-manual/html_node/Library-Headers.html
 * http://www.emacswiki.org/cgi-bin/wiki/ElispAreaConventions

CheckDoc.
---------

CheckDoc checks your EmacsLisp code for errors in documentation and style.

  http://cedet.sourceforge.net/checkdoc.shtml
                home page before including it into GNU Emacs
  http://www.emacswiki.org/emacs/CheckDoc
                CheckDoc

Installing Emacs.
=================

From sources.
-------------

 * http://ftp.gnu.org/pub/gnu/emacs

Windows.
--------

  http://ftp.gnu.org/pub/gnu/emacs/windows
                Releases for Windows.
  http://alpha.gnu.org/gnu/emacs/windows
                Beta releases for Windows.

Debian.
-------
::

  $ apt-get install emacs

Emacs paths.
============
::

  source-directory data-directory doc-directory exec-directory
  invocation-directory trash-directory tutorial-directory user-emacs-directory
  widget-image-directory

Emacs games.
============
::

  hanoi hanoi-unix life pong tetris gomoku

Long lines.
===========
::

  (setq longlines-show-hard-newlines t)
  (setq longlines-wrap-follows-window-size t)
  (longlines-mode 1)

Printing Emacs structures.
==========================
::

  (message "%S" '(a b 123 "hello" 'set))
  (pp '(a b 123 "hello" 'set))
  (prin1-to-string '(1 2))

  (symbol-name 'f)
  (symbol-value 'f)
  (symbol-function 'f)
  (symbol-plist 'f)

  (local-variable-p var buffer)

File manager.
=============

 * http://www.emacswiki.org/emacs/Sunrise_Commander

Semantic.
=========

  semantic-lex-spp-describe
                Describe the current list of spp macros.
  semantic-lex-c-preprocessor-symbol-file
                List of C/C++ files that contain preprocessor macros for the C lexer.

Debugging C code.
=================
::

  -*- mode: grep; mode: auto-revert-tail; default-directory: "~/devel/proj" -*-

XML modes.
==========

XSLT-process.
-------------

XSLT-process is a minor mode for GNU Emacs/XEmacs which transforms it into a powerful editor with
XSLT processing and debugging capabilities.

The mode currently supports two Java XSLT processors:

 * Saxon - fully supported, including debugging capabilities.
 * Xalan - fully supported, including debugging capabilities.

  http://xslt-process.sourceforge.net/
                home page

Useful program logging.
=======================

Put first line to your log file, you must replace ``default-directory`` to dir where you build
program::

  -*- mode: compilation-minor; mode: auto-revert-tail; default-directory: "~/devel/proj" -*-

Program must use one of supported by ``compilation-minor-mode`` (see
``compilation-error-regexp-alist``), like::

  printf(__FILE__ ":%d: %s\n", __LINE__, msg);  /* msg - user defined string */

or in second form (in this case line number included in format string, so easy searchable in
debugger)::

  #define NUM2STR(x) STR(x)
  #define STR(x) #x

  printf(__FILE__ ":" NUM2STR(__LINE__) ": %s\n", msg);

Or some faster use ``grep-mode``, but you restricted with GNU like error format::

  -*- mode: grep; mode: auto-revert-tail; default-directory: "~/devel/proj" -*-

Edit HTML.
==========

 * psgml-mode
 * nxml-mode
 * sgml-mode

html-helper-mode.
-----------------

Highlighting, autocompletion, and auto-insertion of closing tags.

 * http://www.emacswiki.org/emacs/HtmlHelperMode
 * http://savannah.nongnu.org/projects/baol-hth/
 * http://www.nongnu.org/baol-hth/

Source.
=======

Get main development sources::

  $ bzr init-repo --2a emacs
  $ cd emacs
  $ bzr branch http://bzr.savannah.gnu.org/r/emacs/trunk trunk
  $ cd trunk
  $ bzr bind http://bzr.savannah.gnu.org/r/emacs/trunk

To update with latest changes::

  $ cd emacs/trunk
  $ bzr update

See:

 * http://www.emacswiki.org/emacs/BzrForEmacsDevs

Emacs Git mirror.
-----------------

 * http://www.emacswiki.org/emacs/EmacsFromGit

Patch.
======

  http://debbugs.gnu.org/cgi/bugreport.cgi?bug=5719
                [patch] fix bat-generic-mode highlighting pattern for CLI
                switch.

How report bug.
===============

Visit http://debbugs.gnu.org or ``M-x report-emacs-bug``.

Finding emacs packages.
=======================

 * http://anc.ed.ac.uk/~stephen/emacs/ell.html
 * http://www.emacswiki.org/emacs/WikifiedEmacsLispList
 * http://www.emacswiki.org/emacs/RationalElispPackaging

  http://tromey.com/elpa/index.html
                Emacs Lisp Package Archive


EPLA.
-----

ELPA goal is to make it simple to install, use, and upgrade Emacs Lisp packages.

Currently (2011-02-15) available such sources::

  (setq package-archives '(("ELPA" . "http://tromey.com/elpa/")
                           ("gnu" . "http://elpa.gnu.org/packages/")
                           ("marmalade" . "http://marmalade-repo.org/packages/")
                           ))

 * http://www.emacswiki.org/emacs/ELPA
 * http://marmalade-repo.org/

  http://elpa.gnu.org/
                official GNU Emacs Lisp Package Archive
  http://tromey.com/elpa/
                old Emacs Lisp Package Archive home page
  http://tromey.com/elpa/upload.html
                how to contribute

Emacswiki.
----------

 * http://www.emacswiki.org/emacs/ElispArea
 * http://www.emacswiki.org/emacs/WikifiedEmacsLispList

emacsmirror.
------------

 * https://github.com/emacsmirror/p/wiki
 * http://www.emacsmirror.org/
 * http://www.emacswiki.org/emacs/Emacsmirror

Funny Emacs modes.
==================

  glasses
                Minor mode for making identifiers likeThis readable.

Useful commands.
================
::

  flush-lines keep-lines
  align-regexp
  C-x C-o
  M-PageUp/M-PageDown
  command-history
  M-=
  C-x l
  locate-library find-library
  features load-history

