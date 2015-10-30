.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 Display.
==========
.. contents::

Native display resolutions.
===========================

  19"    4:3    SXGA    1280х1024
  20"    4:3    UXGA    1600x1200
  21"    4:3    UXGA    1600x1200
  22"   16:10   WUXGA   1920x1200
  24"   16:10   WUXGA   1920x1200
  26"   16:10   WUXGA   1920x1200
  30"   16:10   WQXGA   2560x1600

Selecting display.
==================

  http://www.100fps.com/how_many_frames_can_humans_see.htm
                How many frames per second can the human eye see?
  http://www.tftcentral.co.uk/articles/panel_parts.htm
                Panel Part Databases
  http://www.tftcentral.co.uk/panelsearch.htm
                Panel Search

ICC Profiles.
=============

 * https://wiki.archlinux.org/index.php/ICC_Profiles

PC display modes.
=================

VESA standards (SUPER VGA).
---------------------------

  640x480 text & graphics (256-16M colors)
  800x600 text & graphics (16-16M colors)
  1024x768 text & graphics (16-16M colors)
  1280x1024 text & graphics (16-16M colors)

IBM standards.
--------------

  MDA   720x350 text only, monochrome
  CGA   320x200 text & graphics (4 colors)
  EGA   640x350 text & graphics (16 colors)
  MCGA  640x400 text; 320x200 graphics (256 cols)
  VGA   720x400 text; 640x480 graphics (16 colors)
  8514 1024x768 text & graphics (256 colors)
  XGA  1024x768 text & graphics (256 colors)

Hercules standard.
------------------

  720x348 text & graphics (monochrome)

VESA modes.
-----------

  VESA BIOS Extension (VBE)
  Super VGA modes defined by VESA

  Mode no.                  Video
  Dec. Hex  Res.    Colors  RAM used
  256  100  640x400   256   250K
  257  101  640x480   256   300K

  258  102  800x600    16   234K
  259  103  800x600   256   469K

  260  104  1024x768   16   384K
  261  105  1024x768  256   768K

  262  106  1280x1024  16   640K
  263  107  1280x1024 256  1280K

  264  108   80x60 text     9.3K
  265  109  132x25 text     6.4K
  266  10A  132x43 text    11.1K
  267  10B  132x50 text    12.9K
  268  10C  132x60 text    15.5K

  269  10D  320x200   32K   125K
  270  10E  320x200   64K   125K
  271  10F  320x200   16M   188K

  272  110  640x480   32K   600K
  273  111  640x480   64K   600K
  274  112  640x480   16M   900K

  275  113  800x600   32K   938K
  276  114  800x600   64K   938K
  277  115  800x600   16M  1406K

  278  116  1024x768  32K  1536K
  279  117  1024x768  64K  1536K
  280  118  1024x768  16M  2304K

  281  119  1280x1024 32K  2560K
  282  11A  1280x1024 64K  2560K
  283  11B  1280x1024 16M  3840K

      81FF  Special mode to save
            and restore video RAM.


Note: As of VBE 2.0, VESA no longer defines new modes by number. It provides a mechanism for defining the mode by resolution.

  Number    Pixel bits
  colors    R  G  B
  32K       5  5  5
  64K       5  6  5
  16M       8  8  8


Earlier IBM modes.
------------------

  Mode
  No. CGA
  0   320x200  40x25 txt  16 gray
  1   320x200  40x25 txt  16 colors
  2   640x200  80x25 txt  16 gray
  3   640x200  80x24 txt  16 colors
  4   320x200  graphics    4 colors
  5   320x200  graphics    4 gray
  6   640x200  graphics   monochrome

  EGA
  0   320x350  40x25 txt  16 gray
  1   320x350  40x25 txt  16 colors
  2   640x350  80x25 txt  16 gray
  3   640x350  80x25 txt  16 colors
  7   720x350  80x25 txt  monochrome
  13  320x200  graphics   16 colors
  14  640x200  graphics   16 colors
  15  640x350  graphics   monochrome
  16  640x350  graphics   16 colors

  MCGA
  0   320x400  40x25 txt  16 gray
  1   320x400  40x25 txt  16 colors
  2   640x400  80x25 txt  16 gray
  3   640x400  80x25 txt  16 colors
  17  640x480  graphics   monochrome
  19  320x200  graphics   256 colors

  VGA
  0   360x400  40x25 txt  16 gray
  1   360x400  40x25 txt  16 colors
  2   720x400  80x25 txt  16 gray
  3   720x400  80x25 txt  16 colors
  7   720x400  80x25 txt  monochrome
  18  640x480  graphics   16 colors

  XGA
  640x480   graphics   256 colors
  640x480   graphics   64K colors
  1024x768  graphics   256 colors


