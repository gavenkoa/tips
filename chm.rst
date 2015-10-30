.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

======
 CHM.
======
.. contents::

Spec.
=====

  http://www.nongnu.org/chmspec/
    HTML Help Projects.
  http://chmspec.nongnu.org/
    HTML Help Projects.
  http://chmspec.nongnu.org/latest/
    Unofficial (Preliminary) HTML Help Specification.
  http://savannah.nongnu.org/projects/chmspec
    Unofficial CHM Specification.
  http://www.speakeasy.org/~russotto/chm/chmformat.html
    Matthew Russotto's Microsoft's HTML Help format description.
  http://msdn.microsoft.com/en-us/library/ms669980.aspx
    HTML Help Frequently Asked Questions.
  http://kb.helpwaregroup.com/ms-html-help/hh_info
     HH Info, version history
  http://kb.helpwaregroup.com/ms-html-help/hh-faq
     FAQ


Alternatives.
=============

  http://www.imendio.com/projects/devhelp/
    DevHelp is a GNOME based online help system aimed toward developers.
  http://en.wikipedia.org/wiki/MHTML
    MHTML, short for MIME HTML.

 * https://en.wikipedia.org/wiki/Online_help
 * https://en.wikipedia.org/wiki/List_of_help_authoring_tools

Microsoft HTML Help.
====================

  https://msdn.microsoft.com/en-us/library/ms669985
    Microsoft HTML Help Downloads.
  http://www.microsoft.com/en-us/download/details.aspx?id=21138
    HTML Help Workshop and Documentation.
  http://support.microsoft.com/kb/269766/
    INFO: Limited Unicode Support in HTML Help.
  http://www.help-info.de/en/Help_Info_HTMLHelp/hh.htm
    Various links.

Microsoft HTML Help under Debian.
=================================

Set Wine's Windows version to Windows 2000 (or above) via ``winecfg``.

Install necessary dependency::

  $ winetricks mfc40

Alternatively manually download and install `Microsoft Foundation Classes update
<http://activex.microsoft.com/controls/vc/mfc40.cab>`_::

  $ wget http://activex.microsoft.com/controls/vc/mfc40.cab
  $ cabextract mfc40.cab
  $ wine mfc40.exe

Download `Microsoft HTML Help Workshop
<https://msdn.microsoft.com/en-us/library/ms669985.aspx>`_ and install it as
(from non-``noexec`` FS!!)::

  $ wine htmlhelp.exe

Install ``itircl.dll`` and ``itss.dll`` from ``hhupd.exe`` which available in
installer or in ``~/.wine/drive_c/Program Files/HTML Help Workshop/redist``::

  cabextract -F hhupd.exe htmlhelp.exe
  cabextract -F itircl.dll hhupd.exe
  cabextract -F itss.dll hhupd.exe
  cp -a itircl.dll ~/.wine/drive_c/windows/system32/
  cp -a itss.dll ~/.wine/drive_c/windows/system32/

You must add exception for ``hhc.exe`` and ``hhw.exe`` to use native variant of
``itss.dll`` via ``winecfg``. Note: don't set ``itss.dll`` to native by default
becase then ``wine hh`` wouldn't work.

See:

 * http://code.google.com/p/htmlhelp/wiki/HHW4Wine
 * https://appdb.winehq.org/objectManager.php?sClass=version&iId=2978
 * https://bugs.winehq.org/show_bug.cgi?id=7517

Viewer.
=======
::

  $ sudo apt-get install xchm
  $ sudo apt-get install gnochm

  $ wine hh $FILE

Decompiler.
===========

For Windows::

  cmd> hh.exe -decompile %OUTDIR% %INFILE%.chm
  cmd> 7z x -o%OUTDIR% %INFILE%.chm

Under Linux::

  $ 7z x -o$OUTDIR $INFILE.chm

  $ sudo apt-get install libchm-bin
  $ extract_chmLib $INFILE.chm $OUTDIR


Cyrillic CHM files.
===================

In order to show Cyrillic tests in ``hh.exe`` or ``xchm``:

 * Use ``cp1251`` or ``cp866`` encoding for ``.html`` files.

 * Place corresponding::

     <meta http-equiv="Content-Type" content="text/html; charset=cp1251">

   or::

     <meta http-equiv="Content-Type" content="text/html; charset=cp866">

   into into ``<head>`` tag of  your ``.html`` files.

 * Use ``cp1251`` encoding for ``.hhc`` and ``.hhk`` and ``.stp`` files.

 * Add correcponding settings into your ``.hhp`` file::

     [OPTIONS]
     Language=0x419 Russian

``<meta charset="cp1251">`` works for ``hh.exe`` but not for ``xchm``.

Because ``cp1251`` contains all Cyrillic letters while ``cp866`` only Russian
and content/index file require only ``cp1251`` I recommend to use only
``cp1251`` for ``.html`` files.

See:

 * http://kb.helpwaregroup.com/ms-html-help/hh-tips-tricks/jp

