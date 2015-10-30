.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

================
 Code analysis.
================
.. contents::

About.
======

 * http://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis
 * http://en.wikipedia.org/wiki/Static_code_analysis
 * http://en.wikipedia.org/wiki/Automated_code_review
 * http://en.wikipedia.org/wiki/Dynamic_code_analysis
 * http://en.wikipedia.org/wiki/Program_analysis_%28computer_science%29
 * http://en.wikipedia.org/wiki/Performance_analysis
 * http://en.wikipedia.org/wiki/Program_verification

Splint.
=======

Secure Programming Lint, is a programming tool for statically checking C
programs for security vulnerabilities and coding mistakes. Formerly called
LCLint, it is a modern version of the Unix lint tool.

  http://en.wikipedia.org/wiki/Splint_%28programming_tool%29

weblint.
========

Syntax and minimal style checker for HTML.

lintsh.
=======

Lintsh is a Bourne shell that optionally warns about suspicious or nonportable
constructs.

  http://code.dogmap.org/lintsh/
                Home page.

Valgrind.
=========

Runs programs on a virtual processor and can detect memory errors (e.g., misuse
of malloc and free) and race conditions in multithread programs.

  http://en.wikipedia.org/wiki/Valgrind
                Wikipedia page.

Dmalloc.
========

Dmalloc is a memory debugger C library.

  http://en.wikipedia.org/wiki/Dmalloc

Avalanche.
==========

Avalanche is a dynamic defect detection tool that generates "inputs of death" -
input data reproducing critical bugs and vulnerabilities in the analysed
program.

  http://code.google.com/p/avalanche/
                Home page.
  http://en.wikipedia.org/wiki/Avalanche_%28dynamic_analysis_tool%29
                Wikipedia page.

Sparse.
=======

Sparse is a tool designed to find possible coding faults in the Linux kernel.

  http://en.wikipedia.org/wiki/Sparse
                Wikipedia page.

PMD.
====

PMD is a static ruleset based Java source code analyzer that identifies
potential problems.

PMD has plugins for JDeveloper, Eclipse, JEdit, JBuilder, Omnicore's CodeGuide,
NetBeans/Sun Studio, IntelliJ IDEA, TextPad, Maven, Ant, Gel, JCreator, Hudson,
Jenkins, Sonar and Emacs.

  http://pmd.sf.net/
                Home page.
  http://en.wikipedia.org/wiki/PMD_%28software%29
                Wikipedia page.

Checkstyle.
===========

Static code analysis tool used in software development for checking if Java
source code complies with coding rules.

  http://en.wikipedia.org/wiki/Checkstyle
                Wikipedia page.

FindBugs.
=========

  http://en.wikipedia.org/wiki/FindBugs
                Wikipedia page.

Pychecker.
==========

  http://en.wikipedia.org/wiki/Pychecker
                Wikipedia page.

Pylint.
=======

  http://en.wikipedia.org/wiki/Pylint
                Wikipedia page.

JSLint.
=======

JSLint is a static code analysis tool used in software development for checking
if JavaScript source code complies with coding rules.

It is provided primarily as an online tool, but there are also command-line
adaptations.

  http://en.wikipedia.org/wiki/JSLint
                Wikipedia page.

Squale.
=======

Squale (Software Quality Enhancement) is an open-source platform that helps
monitoring software quality for multi-language applications. It currently
supports Java out-of-the-box, and can also analyse C/C++ and Cobol code with an
adapter to McCabe tool. Squale is distributed under the terms of the LGPL v3
licence.

  http://en.wikipedia.org/wiki/Squale
                Wikipedia page.

Yasca.
======

Yasca leverages external open source programs, such as FindBugs, PMD, JLint,
JavaScript Lint, PHPLint, Cppcheck, ClamAV, Pixy, and RATS to scan specific file
types, and also contains many custom scanners developed for Yasca.

  http://yasca.org/
                Home page.
  http://yasca.org/
                Development home page.
  http://en.wikipedia.org/wiki/Yasca
                Wikipedia page.

Sonar.
======

Sonar uses various static code analysis tools such as Checkstyle, PMD, FindBugs,
Clover to extract software metrics.

  http://en.wikipedia.org/wiki/Sonar_%28software_quality%29
                Wikipedia page.

sloccount.
==========

Count files or LOC in project hierarchy::

  $ sudo apt-get install sloccount
  $ sloccount --addlangall $DIR/$PROJ
  $ rm -r $HOME/.slocdata/$PROJ

