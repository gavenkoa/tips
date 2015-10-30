.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============================
 Development under Windows.
============================
.. contents::

Windows images.
===============

  http://www.modern.ie/en-us/virtualization-tools#downloads
                Test versions of IE using Virtual Machines that you download and
                manage in your own development environment.

Dependency Walker.
==================

Dependency Walker is a free utility that scans any 32-bit or 64-bit Windows
module (exe, dll, ocx, sys, etc.) and builds a hierarchical tree diagram of
all dependent modules. For each module found, it lists all the functions that
are exported by that module, and which of those functions are actually being
called by other modules. Another view displays the minimum set of required
files, along with detailed information about each file including a full path
to the file, base address, version numbers, machine type, debug information,
and more.

See:

 * http://www.dependencywalker.com/

Windows 2000 Resource Kit Tools.
================================

  http://support.microsoft.com/kb/927229
                Windows 2000 Resource Kit Tools for administrative tasks

Sysinternals.
=============

TODO

Application verifier.
=====================

  http://www.microsoft.com/downloads/en/details.aspx?familyid=c4a25ab9-649d-4a1b-b4a7-c9d8b095df18
                download page
  http://msdn.microsoft.com/en-us/library/ms220948.aspx
                Application Verifier

Debugging with windbg.
======================

  http://www.microsoft.com/whdc/devtools/debugging/default.mspx
                Download and Install Debugging Tools for Windows
  http://www.microsoft.com/whdc/devtools/debugging/installx86.mspx
                Debugging Tools for Windows 32-bit Version
                download page
  http://www.microsoft.com/whdc/devtools/debugging/install64bit.mspx
                Debugging Tools for Windows 64-bit Version
                download page

Break on dll load/unload.
-------------------------
::

  sxe ld <module>
  sxe ud <module>

Set breakpoint by pattern and/or on specific module.
----------------------------------------------------
::

  bm <module>!<name>    # set breakpoints on 'module' with name 'name'
  bm *!<prefix>*        # set breakpoints on all names with prefix 'prefix'
  bm <module>!*         # set breakpoints on all names in module 'module'

``bp``, ``bm`` commands sets software breakpoints, debugger replaces the processor
instruction with a break instruction.

Clear breakpoints.
------------------
::

  bc *

How to set WinDbg as a Default Windows Postmortem Debugger.
-----------------------------------------------------------
::

  cmd> WinDbg -I

How analyse crash.
------------------

When program crash and use enter in WinDbg execute::

  !analyze -v

Adding symbols from Symbol Server.
----------------------------------

Execute in WinDbg::

  .sympath SRV*D:\srv\symcache*http://msdl.microsoft.com/download/symbols

or Ctrl+S and add::

  SRV*D:\srv\symcache*http://msdl.microsoft.com/download/symbols

See:

  http://support.microsoft.com/kb/311503
                Use the Microsoft Symbol Server to obtain debug symbol files

Using the SymChk.exe utility to download symbols.
-------------------------------------------------
::

  symchk /r c:\windows\system32 /s SRV*c:\symbols\*http://msdl.microsoft.com/download/symbols

Debugging child process.
------------------------
::

  .childdbg 1

Running at startup.
===================

  HKCU\Software\Microsoft\Windows\CurrentVersion\Run
                Launches a program automatically when a particular user logs
                in. This key is used when you always want to launch a program
                when a particular user is using a system.
  HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
                Launches a program the next time the user logs in and removes
                its value entry from the registry. This key is typically used
                by installation programs.
  HKLM\Software\Microsoft\Windows\CurrentVersion\Run
                Launches a program automatically at system startup. This key
                is used when you always want to launch a program on a
                particular system.
  HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce
                Launches a program the next time the system starts and removes
                its value entry from the registry. This key is typically used
                by installation programs.
  HKLM\Software\Microsoft\Windows\CurrentVersion\RunServices
                Launches a service (a standard NT service or a background
                process) automatically at startup. An example of a service is
                a Web server such as Microsoft Internet Information Server.
  HKLM\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce
                Launches a service (a standard NT service or a background
                process) the next time the system is started, then removes its
                value entry from the registry.

Values to registry on Windows XP can be added by::

  cmd> reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run" /v run.bat /t REG_SZ /d "path\to\run.bat"
  cmd> reg query HKCU\Software\Microsoft\Windows\CurrentVersion\Run   <-- see what done

Cabinet file (.cab).
====================

Extract content from .cab file::

  cmd# expand my.cab

See:

  http://support.microsoft.com/kb/198038
                INFO: Useful Tools for Package and Deployment Issues
  http://msdn.microsoft.com/en-us/library/aa367841%28VS.85%29.aspx
                The Makecab.exe utility is included in the Windows SDK
                Components for Windows Installer Developers.
  http://web.archive.org/web/20070403215326/http://download.microsoft.com/download/platformsdk/cab/2.0/w98nt42kmexp/en-us/cabsdk.exe
                download link from web archive
  http://msdn.microsoft.com/en-us/library/aa370834%28v=VS.85%29.aspx
                The components of the Windows Installer Software Development
                Kit are included in the Microsoft Windows Software Development
                Kit (SDK).
  http://msdn.microsoft.com/en-us/library/bb417343.aspx
                Microsoft Cabinet Format

Internet Explorer.
==================

Debugging IE.
-------------

Install IE 8.0 and press 'F12' key.

  http://msdn.microsoft.com/library/dd565626.aspx
                Developer Tools User Interface Reference

Microsoft technologies.
=======================

COM.
----

The family of COM technologies includes COM+, Distributed COM (DCOM) and
ActiveX® Controls.

  http://www.microsoft.com/com/default.mspx
                home page

OLE.
----

OLE (Object Linking and Embedding) allows embedding and linking to documents and
other objects.

OLE 1.0 released in 1990, OLE 2.0 released in 1993, in 1994 OLE custom controls
(OCXs) were introduced.

OLE objects and containers are implemented on top of the Component Object Model.

Next release after 2.0 introdused in 1996 and named as ActiveX.

 * http://en.wikipedia.org/wiki/Object_Linking_and_Embedding

ActiveX.
--------

Faced with the complexity of OLE 2.0 and with poor support for COM in MFC,
Microsoft rationalized the specifications to make them simpler, and rebranded
the technology as ActiveX in 1996.

  http://msdn.microsoft.com/en-us/library/aa751968.aspx
                ActiveX Controls.
  http://en.wikipedia.org/wiki/ActiveX
                Wikipedia article.

ATL.
----

The Active Template Library (ATL) is a set of template-based C++ classes
developed by Microsoft, intended to simplify the programming of Component Object
Model (COM) objects.

  http://en.wikipedia.org/wiki/Active_Template_Library

MFC.
----

MFC (Microsoft Foundation Classes) is a library that wraps portions of the
Windows API in C++ classes, including functionality that enables them to use a
default application framework. Classes are defined for many of the
handle-managed Windows objects and also for predefined windows and common
controls.

A lightweight alternative to MFC is the Windows Template Library (WTL).

 * http://en.wikipedia.org/wiki/Microsoft_Foundation_Class_Library
 * http://ru.wikipedia.org/wiki/Microsoft_Foundation_Classes

Can I link to MFC statically.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, see:

 * http://msdn.microsoft.com/en-us/library/f22wcbea%28VS.80%29.aspx

Microsoft Visual C++ Redistributable Package.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en
                This package installs runtime components of C Runtime (CRT),
                Standard C++, ATL, MFC, OpenMP and MSDIA libraries.

WTL.
====

WTL (Windows Template Library) is a free software, object-oriented C++ template
library for Win32 development.

WTL provides support for implementing various user interface elements, to MDI,
standard and common controls, common dialogs, property sheets and pages, GDI
objects, and other common UI elements, such as scrollable windows, splitter
windows, toolbars and command bars.

Most of the WTL API is a mirror of the standard Win32 calls.

 * http://sourceforge.net/projects/wtl
 * http://en.wikipedia.org/wiki/Windows_Template_Library

Windows style variable names.
=============================
::

  Prefix   |  Data type
  ---------+-----------------------------------------
  b        |  boolean
  by       |  byte or unsigned char
  c        |  char
  cx / cy  |  short used as size
  dw       |  DWORD, double word or unsigned long
  fn       |  function
  h        |  handle
  i        |  int (integer)
  l        |  Long
  n        |  short int
  p        |  a pointer variable containing the address of a variable
  s        |  string
  sz       |  ASCIIZ null-terminated string
  w        |  WORD unsigned int
  x, y     |  short used as coordinates

::

  PrefixCategory  | Mean
  ----------------+----------------
  CS              | Class style
  CW              | Create window
  DT              | Draw text
  IDC             | Cursor ID
  IDI             | Icon ID
  WM              | Window message
  WS              | Window style

::

  Data type | Meaning
  ----------+-------------------------------------------------------------------
  FAR       | Same as far. Identifies an address that originally used the
            | segment:offset addressing schema. Now FAR simply identifies a
            | (default) 32-bit address but may be omitted entirely in many cases.
            |
  PASCAL    | Same as Pascal. The Pascal convention demanded by Windows
            | defines the order in which arguments are found in the stack when
            | passed as calling parameters.
            |
  WORD	    | Unsigned integer (16 bits)
            |
  UINT      | Unsigned integer, same as WORD
            |
  DWORD     | Double word, unsigned long int (32 bits)
            |
  LONG      | Signed long integer (32 bits)
            |
  LPSTR     | Long (far) pointer to character string
            |
  NEAR      | Obsolete, previously identified an address value within a 16KB
            | memory block.

See:

  http://www.tenouk.com/cnotation.html
                C/C++ NOTATION STORY
