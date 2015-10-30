.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=====================
 Driver for Windows.
=====================
.. contents::

About.
======

  microsoft.public.development.device.drivers
                NNTP driver development group at msnews.microsoft.com:119
  http://www.microsoft.com/communities/newsgroups/list/en-us/default.aspx
                Web-interface to NNTP forum

Which version exist?
====================

 - VxD
                Windows 3.x and Windows 9x
 - Windows Driver Model (WDM)
                Windows 98, Windows 98 Second Edition, Windows Me, Windows
                2000, Windows XP, Windows Server 2003 and Windows Vista (for
                backwards compatibility)
 - Windows Driver Foundation (WDF)
                Windows 2000 and later

  http://en.wikipedia.org/wiki/VxD
                VxD
  http://en.wikipedia.org/wiki/Windows_Driver_Model
                WDM.
  http://en.wikipedia.org/wiki/Windows_Driver_Foundation
                WDF.

Msinfo32.exe.
=============

Windows XP/2003 System Information Tool.

 * http://support.microsoft.com/kb/308549

Sysinternals.
=============

WinObj.
-------

Winobj is a program that lets you browse the Windows NT Object Manager
namespace.

devtree.
--------

The DeviceTree V2.12 utility is a Windows XP/Server 2003 utility written by
OSR, that allows the user the ability to display the drivers and devices
loaded in 2 different views. The first view Driver View the user sees a list
of all the drivers loaded in kernel mode and all the devices that those
drivers have created. In the second view PnP View the user sees a list of all
the devices in the system from that of Plug and Play Manager (PnP).

Microsoft DDK.
==============

DevCon.
-------

Supported device classes::

  cmd> devcon.exe classes

Which files used by specific driver (with "*" prints list of files for all
drivers)::

  cmd> devcon.exe driverfiles *

Device ID (names included)::

  cmd> devcon.exe hwids *

Device status (running/stoped)::

  cmd> devcon.exe status *

USB Command Verifier.
=====================

All USB peripherals are required to pass the Device Framework tests in order
to gain certification.

 * http://www.usb.org/developers/tools/

Files.
======

Windows 98 SE/ME.
-----------------

 * .386
   VxD driver under Windows 3.x
 * .vxd
   VxD driver under Windows 95

Windows NT (2000/XP/2003).
--------------------------

 * .inf
   Stored in %Windir%\Inf.
 * .pnf
   Precompiled INF File. Stored in %Windir%\Inf.

Driver type.
============

CDC.
----

  http://support.microsoft.com/kb/837637
                How to use or to reference the Usbser.sys driver from
                universal serial bus (USB) modem .inf files.

Driver class.
=============

  http://msdn.microsoft.com/en-us/library/ms791134.aspx
                System-Supplied Device Setup Classes
  http://msdn.microsoft.com/en-us/library/ff538820.aspx
                Drivers for the Supported USB Device Classes

How list drivers?
=================

Set environment devmgr_show_nonpresent_devices to 1 and run Device Manager,
select "View" --> "Show hidden devices".

How install drivers?
====================

dpinst.
-------

Driver Install Frameworks (DIFx) tools allow installing driver under following
OSes:

  Windows Server 2008 R2
  Windows 7
  Windows Server 2008
  Windows Vista
  Windows Server 2003
  Windows XP
  Windows 2000

It consist from API (from library, DIFxAPI, DIFxApp) and command line tool
(DPInst) which can be found in WDK and their licence allow redistribution.

  http://www.microsoft.com/whdc/driver/install/DIFxFAQ.mspx
                Information about Driver Install Frameworks Tools
  http://msdn.microsoft.com/ru-ru/magazine/cc302206%28en-us%29.aspx
                If you update any drivers in Device Manager
                %windir%\system32\ReinstallBackups folder is created with
                backups of the old drivers.

devcon.
-------

This command-line specifies the location of the driver package's INF file (c:\toaster\toastpkg.inf)
and the toaster device's hardware identifier (ID), which is specified within the INF file::

  cmd# devcon.exe install c:\toaster\toastpkg.inf {b85b7c50-6a01-11d2-b841-00c04fad5171}\mstoaster

See:

  http://msdn.microsoft.com/en-us/library/ff553642.aspx
                Using the DevCon Tool to Install a Driver Package

How debug Windows drivers.
==========================

To detect whether a driver loaded, check the status of the device in Device Manager.

SetupAPI logs information about device installation in a plain-text log file
that you can use to verify the installation of a device and to troubleshoot
device installation problems.

For Windows XP/2003 check::

  %SystemRoot%/setupapi.log

For Windows Vista and later versions of Windows check::

  %SystemRoot%\inf\SetupAPI.dev.log     installation events in the device
  %SystemRoot%\inf\SetupAPI.app.log     application installation

See:

  http://msdn.microsoft.com/en-us/library/ff553497.aspx
                Troubleshooting Install and Load Problems with Signed Driver Packages
  http://www.microsoft.com/whdc/devtools/debugging/debugtips.mspx
                Improve Driver Debuggability
  http://msdn.microsoft.com/en-us/library/ff551063.aspx
                Debugging Tools for Windows
  http://msdn.microsoft.com/en-us/library/ff543450%28VS.85%29.aspx
                Checked and Free Build Differences
  http://msdn.microsoft.com/en-us/library/windows/hardware/ff540793.aspx
                Debugging Driver Installation
  http://msdn.microsoft.com/en-us/library/windows/hardware/ff550863.aspx
                SetupAPI Device Installation Log Entries

Driver signing.
===============

Type of signature:

 * Signed by a Windows signing authority.
 * Signed by a trusted publisher.
 * Signed by an untrusted publisher.
 * Signed by a publisher of unknown trust.
 * Altered.
 * Unsigned.

  http://msdn.microsoft.com/en-us/library/ff544703.aspx
                Type of signature and performed action.
  http://www.microsoft.com/whdc/driver/install/drvsign/best-practices.mspx
                Code-Signing Best Practices.
  http://msdn.microsoft.com/en-us/library/ff550764.aspx
                Device Installation Signing Requirements.
  http://www.microsoft.com/whdc/winlogo/categories.mspx
                Windows Logo Program Test Categories.
  http://www.microsoft.com/whdc/driver/install/drvsign/crosscert.mspx
                Root Authority Cross-Certificate List

Disable signing requirement on Windows 7 x64.
=============================================
::

  cmd> bcdedit -set loadoptions DDISABLE_INTEGRITY_CHECKS
  cmd> bcdedit -set TESTSIGNING ON

To revert back::

  cmd> bcdedit.exe -set loadoptions ENABLE_INTEGRITY_CHECKS
  cmd> bcdedit.exe -set TESTSIGNING OFF

Tools for Signing Drivers.
==========================

'certmgr.msc' present in Windows 2000 and upper.

From Windows SDK/WDK::

  CertMgr Inf2Cat MakeCat MakeCert Pvk2Pfx SignTool

To register certificate in Windows 7 (or install "Admin Tools Pack" in Windows
XP)::

  cmd> certutil -addstore TrustedPublisher cert.cer

See:

  http://msdn.microsoft.com/en-us/library/ff552958.aspx
                Tools for Signing Drivers
  http://www.microsoft.com/download/en/details.aspx?id=16770
                Admin Tools Pack

Invoking a Device Properties Dialog Box from a Command-line Prompt.
===================================================================

You need get device-instance-ID-parameter::

  cmd# rundll32.exe devmgr.dll,DeviceProperties_RunDLL /DeviceID "ACPI\PNP0F03\4&1A8C8C2E&0"

 * http://msdn.microsoft.com/en-us/library/ff548170.aspx

Driver Selection Process.
=========================

Windows uses the following criteria to select a driver for a device:

 * Windows selects the driver that has the lowest rank value as the best match for the device.
 * For drivers that have equal rank, Windows selects the driver that has the most recent date.
 * For the drivers that have equal rank and date, Windows selects the driver that has the highest version.
 * Windows XP SP1 and later: For drivers that have equal rank, date, and version, Windows can select any driver.
 * Windows XP and Windows 2000: For drivers that have equal rank, date, and version, Windows can select any driver.

See:

 * http://msdn.microsoft.com/en-us/library/ff549553.aspx

Distributing a Driver Package.
==============================

Windows Update.
---------------

You can distribute a driver package through the Windows Update program if the driver package:

 * Passes the WHQL test program and receives a WHQL release signature.
 * Qualifies for the Windows Logo program.
 * Meets additional requirements that ensure that Windows Update can determine the correct driver
   package for the user's device, can legally distribute it, and can automatically download it.

See:

 * http://msdn.microsoft.com/en-us/library/ff554874.aspx

Hardware ID.
------------

PCI and AGP buses: Contain subsystem ID and subsystem vendor ID (&SUBSYS in the ID string). Drivers
must have VID/DID/SVID/SID PNP ID entries to be published via Windows Update.

PCI Device Subsystem IDs and Windows specifications are available at:

 * http://www.microsoft.com/whdc/archive/pciidspec.mspx

PCMCIA: Always specific; contains PCMCIA in the ID string.

USB: Contains VID and &PID in the ID string.

IEEE 1394: Always specific; contains 1394 in the ID string.

HID: Contains &VID and &PID in the ID string.

IDE: Contains IDE\ in the ID string.

Parallel Port Printers: Contain LPTENUM\ in the ID string.

IrDA Printers: IDs begin with HWP.

  http://www.microsoft.com/whdc/winlogo/winup/default.mspx
                Windows Update Driver Publishing
