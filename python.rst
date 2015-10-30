.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Python
========
.. contents::

Licence and history of Python.
==============================

  http://docs.python.org/dev/license.htm

Byte compile .py and check for errors.
======================================
::

  $ python -m compileall $dir

Install python modules/packages.
================================

  http://wiki.python.org/moin/CheeseShopTutorial
                Installing Distributions from the Python Package Index (Start Here)

Uninstall python modules.
=========================

Install again and save list of installed files::

  $ python setup.py install --record files.txt
  $ rm `cat files.txt`

  http://peak.telecommunity.com/DevCenter/EasyInstall#uninstalling-packages
                Uninstalling Packages

Generate documentation from Python sources.
===========================================

Generate documentation from Python sources by pydoc.
----------------------------------------------------
::

  $ mkdir html
  $ cd html
  $ pydoc -w ../

Generate documentation from Python sources by epydoc.
-----------------------------------------------------

Generate documentation from Python sources by Sphinx.
-----------------------------------------------------
::

  $ sudo apt-get install python-sphinx
  $ sudo apt-get install rst2pdf

Code analyzers and style checkers.
==================================

Pylint.
-------

  http://www.logilab.org/857
  http://pypi.python.org/pypi/pylint

PyChecker.
----------

  http://pychecker.sourceforge.net/

Debugging Python code.
======================

Pretty print under Python.
--------------------------
::

  import pprint
  print(pprint.pformat('string'))
  print(pprint.pformat(['1', '2']))

See:

  http://docs.python.org/library/pprint.html
                Doc page.

Trace Python execution.
=======================

  http://python-ptrace.hachoir.org/trac
                python-ptrace by Victor Stinner
  http://subterfugue.org/
                subterfugue

