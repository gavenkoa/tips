.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========================
 Microsoft visual studio.
==========================
.. contents::

Downloads.
==========

MSVC.
-----

Starting from 2008 MSDN no longer distributed in .iso files. To install help use
"Help Library Manager".

  http://vshelpdownloader.codeplex.com/
                Tool for downloading base Visual Studio 2010 MSDN package for
                offline first installation.

SDK.
----

  http://msdn.microsoft.com/en-us/windows/bb980924.aspx
                Windows SDK

Register SDK to Visual Studio.
==============================

To check all available version::

  cmd> cd %PROGRAMFILES%\Microsoft SDKs\Windows\vX.X\Setup\
  cmd> WindowsSdkVer.exe -version

To check current used version::

  cmd> cd %PROGRAMFILES%\Microsoft SDKs\Windows\vX.X\Setup\
  cmd> WindowsSdkVer.exe -current

Register SDK::

  cmd> cd %PROGRAMFILES%\Microsoft SDKs\Windows\vX.X\Setup\
  cmd> WindowsSdkVer.exe -version:v6.1

MSVC versions.
==============


  NAME                       VER  _MSC_VER  cl
  ========================== ==== ========  =====
  Visual Studio 6.0 (1998)   6.0  1200
  Visual Studio .NET (2002)  7.0  1300
  Visual Studio .NET 2003    7.1  1310
  Visual Studio 2005         8.0  1400      14.00
  Visual Studio 2008         9.0  1500      15.00
  Visual Studio 2010        10.0  1600      16.00

To check version from command line::

  cmd# cl /help 2>&1 | head -n 1
  Microsoft (R) 32-bit C/C++ Optimizing Compiler Version 16.00.30319.01 for 80x8
  cmd# cl /help 2>&1 | head -n 1 | sed "s=.*Version \([0-9]*\)\.\([0-9]*\)\..*=\1.\2="
  16.00

 * http://predef.sourceforge.net/precomp.html#sec35

MFC versions.
=============

  MFC version      Visual C++ version
  ===============  ===================
  1.0              Microsoft C/C++ 7.0
  2.0              Visual C++ 1.0
  2.5              Visual C++ 1.5
  3.0              Visual C++ 2.0
  3.1              Visual C++ 2.1
  3.2              Visual C++ 2.2
  4.0              Visual C++ 4.0
  4.1              Visual C++ 4.1
  4.2              Visual C++ 4.2
  4.21 (mfc42.dll) Visual C++ 5.0
  6.0 (mfc42.dll)  Visual C++ 6.0
  7.0 (mfc70.dll)  Visual C++ .NET 2002
  7.1 (mfc71.dll)  Visual C++ .NET 2003
  8.0 (mfc80.dll)  Visual C++ 2005

  http://msdn.microsoft.com/en-us/library/3z02ch3k.aspx
                ATL and MFC Version Numbers

ALT version.
============

  ATL version   Visual C++ version
  ============= ===================================================
  1.0, 1.1, 2.0 None. Released to Web in Visual C++ 4.x time frame.
  3.0           Visual C++ 6.0
  7.0           Visual C++ .NET 2002
  7.1           Visual C++ .NET 2003
  8.0           Visual C++ 2005

  http://msdn.microsoft.com/en-us/library/3z02ch3k.aspx
                ATL and MFC Version Numbers

MS SDK version.
===============

                                                    VER

Included in Visual Studio 2005                      v5.0
Included in Visual Studio 2008                      v6.0A
SDK Update for Windows Vista
SDK for Windows Server 2008 and .NET Framework 3.5  v6.1
Included in Visual Studio 2010 Express              v7.0A
SDK for Windows 7 and .NET Framework 3.5 SP 1       v7.0
SDK for Windows 7 and .NET Framework 4              v7.1

  http://msdn.microsoft.com/en-us/windows/dd146047.aspx
                Which SDK do I install?
  http://en.wikipedia.org/wiki/Microsoft_Windows_SDK#Versions
                Microsoft Windows SDK Versions

MSVC and SDK compatibility.
===========================

v6.1: MSVC 2005, 2008 + express
v7.0: MSVC 2008 + express
v7.1: MSVC 2005, 2008, 2010 + express

Build MSVC project from command line.
=====================================
::

  cmd> cd %proj%
  cmd> %WINDIR%\Microsoft.NET\Framework\v2.0.50727\msbuild.exe  file.sln

'msbuild.exe' can not upgrade Visual Studio project files, so you better use 'vcbuild.exe' (which
present in MSVC version 8.0/9.0)::

  cmd> cd %proj%
  cmd> %MSVC_ROOT%\VC\vcpackages\vcbuild.exe  file.sln
  cmd> %MSVC_ROOT%\VC\bin\amd64\vcbuild.exe  file.vcproj

  cmd> cd %proj%
  cmd> %MSVC_ROOT%\Common7\IDE\devenv.exe  /Clean file.sln
  cmd> %MSVC_ROOT%\Common7\IDE\devenv.exe  /Build file.sln
  cmd> %MSVC_ROOT%\Common7\IDE\devenv.exe  /Deploy file.sln

  http://msdn.microsoft.com/en-us/library/ms164311.aspx
                MSBuild Command Line Reference
  http://msdn.microsoft.com/en-us/library/kdxzbw9t.aspx
                VCBUILD Command Line
  http://msdn.microsoft.com/en-us/library/xee0c8y7.aspx
                Devenv Command Line Switches

Check linking problem.
======================

Use '/verbose:lib' to see list of libraries for linking and thier order.

Buy MSVC.
=========

  http://msdn.microsoft.com/ru-ru/subscriptions/subscriptionschart.aspx
                Сравнение подписок MSDN

