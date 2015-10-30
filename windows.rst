.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=============
 Windows OS.
=============
.. contents::

Determining windows version.
============================

Run winver.exe: <Win> + R winver <RET>.

Or type: <Win> + <Break>.

Under cmd.exe use built-in command ver.

For Win 2000 and upper check registry key::

  cmd> reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion" /v CurrentVersion

To check 32/64-bit OS use PROCESSOR_ARCHITECTURE env var (it has such values:
x86, AMD64, IA64).

Full info about Windows edition available from this .vbs::

  cmd> slmgr -dli

Windows history.
================

  http://windows.microsoft.com/en-us/windows/history
                A history of Windows

Windows update.
===============

To find updates and drivers visit (подлинность Windows not checked):

  http://catalog.update.microsoft.com/

You can search driver by keywords from Device Manager like::

  VEN_10DE DEV_0247
  VID_22B8 PID_2A62

Also you can find updates on:

  http://www.microsoft.com/downloads/ru-ru/default.aspx

Updates that reset pirate copy of Windows: КВ971033.

List of installed updates::

  cmd> wmic qfe

Check system files integrity.
=============================
::

  cmd> sfc /Scannow

To complete repair you may need original installation CD (you can mount it from
.iso image for example with DemonTools). Look to ``c:/Windows/Logs/CBS/CBS.log``
for errors and warnings.

Works starting from Windows 2000.

See:

 * http://support.microsoft.com/kb/929833
 * http://support.microsoft.com/kb/222471
 * http://support.microsoft.com/kb/310747/ru

Repair boot.
============

If you only damage boot sector of master or system partition boot from Windows
XP installation CD, enter to recovery console and run:

  cmd> fixboot
  cmd> fixmbr

See

  http://support.microsoft.com/kb/307654/ru

Automatically connect to shared resource.
=========================================

Add to autorun such .bat file:

  net use x: \\server\share /user:username password

See

  http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/net_use.mspx

Activate Windows.
=================

Activate Windows from command line::

  cmd> slmgr -ipk YGR45-THIS9-WONT5–0WORK-D7667

Reset the evaluation period/licensing status and activation state of the
machine::

  cmd> slmgr -rearm

Check activation::

  cmd> slmgr /xpr

See:

  http://www.microsoft.com/genuine/selfhelp/XPPkuinst.aspx?sGuid=bab9e103-6365-44dd-9337-93f0cd9dd4b7&displaylang=en
                Windows Product Key Update Tool Instructions

Activate Windows XP.
--------------------

Replace %WINDIR%/system32/winlogon.exe with valid in Safe Mode and run Windows Product Key Update
Tool.

Windows images.
===============

  http://www.microsoft.com/downloads/en/details.aspx?FamilyID=2fcde6ce-b5fb-4488-8c50-fe22559d164e
                Windows XP Service Pack 3 - ISO-9660 CD Image File

Access to Samba from Vista/7.
=============================

By default, you cannot authenticate and share files to and from Mac OS X or
Linux Samba due to a well known authentication method turned off by default.
To enable this,

Only for Windows Vista Ultimate/Business/Enterprise Editions.
-------------------------------------------------------------

Goto Start->Run and open gpedit.msc or secpol.msc

Select Continue on the User Account Control prompt. This will launch the Group
Policy Object Editor for the Local Computer Policy.

In the Group Policy Object Editor, expand:

-> Computer Configuration
-> Windows Settings
-> Security Settings
-> Local Policies
-> Security Options

Open the "Network security: LAN Manager authentication level" policy and
change the Security Setting to:

Send LM & NTLM - use NTLMv2 session security if negotiated

Windows Vista Home Edition.
---------------------------

Since Windows Vista Home Edition does not feature the Group Policy Editor, you
may do the following to enable this feature:

Goto Start->Run-> and type regedit.

Select Continue on the User Account Control prompt.

Navigate to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa

Create the following DWORD value (if it doesn't exist): LmCompatibilityLevel

And set its value to: 1

Map dir to disk.
================

To create::

  cmd> subst [to-disk: [from-disk:]path]

To remove::

  cmd> subst disk: /d

Standard scripts.
=================

  compmgmt.msc - Computer management
  devmgmt.msc - Device manager
  diskmgmt.msc - Disk management
  dfrg.msc - Disk defrag
  eventvwr.msc - Event viewer
  fsmgmt.msc - Shared folders
  gpedit.msc - Group policies
  lusrmgr.msc - Local users and groups
  perfmon.msc - Performance monitor
  rsop.msc - Resultant set of policies
  secpol.msc - Local security settings
  services.msc - Various Services
  msconfig - System Configuration Utility
  regedit - Registry Editor
  msinfo32 - System Information
  sysedit - System Configuration Editor
  win.ini - windows loading information(also system.ini)
  winver - Shows current version of windows
  mailto: - Opens default email client
  command - Opens command prompt

  appwiz.cpl - Add & Remove Programs
  timedate.cpl - Date/Time Properties
  desk.cpl - Display Properties
  inetcpl.cpl - Internet Options
  mmsys.cpl - Sound Settings
  sysdm.cpl - System Properties
  password.cpl - Password Options
  main.cpl - Mouse and Keyboard Options
  control fonts - Fonts Folder
  control printers Printers Folder

'.cpl' scripts can be run from command line as:

  cmd> Rundll32 Shell32.dll,Control_RunDLL
  cmd> Rundll32 Shell32.dll,Control_RunDLL Mmsys.cpl,,0

Path.
=====

Max path length.
----------------

260 chars. Use MAX_PATH macros from 'windows.h'.

Allowed characters.
-------------------

Not allowed:
 * characters from 0 to 31
 * < (less than)
 * > (greater than)
 * : (colon)
 * " (double quote)
 * / (forward slash)
 * \ (backslash)
 * | (vertical bar or pipe)
 * ? (question mark)
 * * (asterisk)

  http://msdn.microsoft.com/en-us/library/aa365247.aspx
                Naming Files, Paths, and Namespaces

Memory.
=======

  http://msdn.microsoft.com/en-us/library/ff542275%28v=VS.85%29.aspx
                Boot Parameters to Configure DEP and PAE

PAE.
----

All 32-bit Windows XP support only 4 GiB RAM. To enable PAE (Physical Address
Extension) edit 'c:\boot.ini', add option '/pae':

  multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="MS Windows XP Prof" /fastdetect /pae

  http://msdn.microsoft.com/en-us/library/ff557168%28v=VS.85%29.aspx
                /pae option
  http://www.microsoft.com/whdc/system/platform/server/pae/paedrv.mspx
                PAE support

NX.
---

NX (no execute) in Windows realised in Data Execution Prevention (DEP)
technology.

On 64-bit processes, DEP is enabled by default and cannot be disabled. For
32-bit Windows DEP is supported in Windows Server 2003 with SP1, Windows XP
with SP2, Windows Vista, and later versions of Windows.

To enable NX on 32-bit Windows edit 'c:\boot.ini', add option
'/noexecute=...' (alwayson/optout/optin/alwaysoff)::

  multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="MS Windows XP Prof" /fastdetect /noexecute=alwayson

To see current DEP status run::

  cmd> wmic OS Get DataExecutionPrevention_Available
  cmd> wmic OS Get DataExecutionPrevention_SupportPolicy
  cmd> wmic OS Get DataExecutionPrevention_Drivers

  http://msdn.microsoft.com/en-us/library/ff557134%28VS.85%29.aspx
                /noexecute parameter
  http://support.microsoft.com/kb/912923
                How to determine that hardware DEP is available and configured on your computer

Windows ISO images.
===================

  http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=25129
                Windows XP Service Pack 3 - ISO-9660 CD Image File

Life cycle.
===========

  http://www.microsoft.com/windows/lifecycle/servicepacks.mspx
                Windows Service Pack Road Map
  http://www.microsoft.com/windows/lifecycle/default.mspx
                Windows Life-Cycle Policy
  http://support.microsoft.com/gp/lifeselect
                Life-Cycle Policy by product
  http://support.microsoft.com/lifecycle/search
                Microsoft Product Lifecycle Search. Type product name into
                search box (like "Windows 95", "Windows XP", "Windows Server
                2003", etc)!

NTFS junction points.
=====================

To craete use 'junction.exe' from Mark Russinovich or 'linkd.exe' from
Microsoft Windows 2000 Resource Kit.

'junction.exe' included with Sysinternals suite.

  cmd> md c:\Program-Files
  cmd> junction c:\Program-Files "c:\Program Files"

  http://technet.microsoft.com/en-gb/sysinternals/bb896768.aspx
                Junction v1.05, Published: July 24, 2007
  http://support.microsoft.com/?kbid=205524
                How to create and manipulate NTFS junction points
  http://en.wikipedia.org/wiki/NTFS_junction_point
                NTFS junction point

Microsoft Windows 2000 Resource Kit.
====================================

  http://support.microsoft.com/kb/927229
                Windows 2000 Resource Kit Tools for administrative tasks
                separate tools downloads

Microsoft security tools.
=========================

  http://www.microsoft.com/downloads/details.aspx?FamilyID=CD057D9D-86B9-4E35-9733-7ACB0B2A3CA1&displayLang=en

  http://www.microsoft.com/downloads/details.aspx?FamilyID=B1E76BBE-71DF-41E8-8B52-C871D012BA78&displayLang=en
                Microsoft Baseline Security Analyzer 2.1.1 (for IT
                Professionals)

  http://www.microsoft.com/downloads/en/confirmation.aspx?familyId=4a2346ac-b772-4d40-a750-9046542f343d&displayLang=en
                Enhanced Mitigation Evaluation Toolkit

  http://blogs.technet.com/b/srd/archive/2009/10/27/announcing-the-release-of-the-enhanced-mitigation-evaluation-toolkit.aspx
                Announcing the release of the Enhanced Mitigation Evaluation
                Toolkit (old version 1.0)

  http://blogs.technet.com/b/srd/archive/2010/07/28/announcing-the-upcoming-release-of-emet-v2.aspx

Enable/Disabling UAC.
=====================

To disable UAC on the computer, you must be able to log on with or provide the
credentials of a member of the local Administrators group.

Starting with Windows 7, UAC is disabled by following these steps:

  1. On the Start menu, type "UAC" and then click Change User Account settings.
  2. Move the slide bar to the bottom (Never Notify) and then click OK.

On Windows Vista and Windows Server 2008, UAC is disabled by following these steps:

  1. Start Control Panel and double-click User Accounts.
  2. In the User Accounts tasks window, click Turn User Account Control on or off.
  3. Clear the Use User Account Control (UAC) to help protect your computer check box, and then click OK.

  http://windows.microsoft.com/en-US/windows-vista/Turn-User-Account-Control-on-or-off
                Turn User Account Control on or off

Fix file association.
=====================

Check current association::

  $ cmd /c assoc | grep -i "^\.mp3"
  .mp3=mp3file

Get list of all available commands::

  $ cmd /c ftype
  ...
  AIMP.mp3="C:\Program Files\AIMP2\AIMP2.exe" "%1"
  ...

and select one on them::

  $ cmd /c assoc .mp3=AIMP.mp3

Clean up Windows system directories.
====================================

Run ``cleanmgr.exe``.

You can safely remove SP restore files::

  %Systemroot%\$NtServicePackUninstall$

Also check such directories::

  %SYSTEMDRIVE%\Program Files\Common Files
  %SYSTEMDRIVE%\Documents and Settings\USER\Application Data
  %SYSTEMDRIVE%\Documents and Settings\USER\Local Settings

  http://support.microsoft.com/kb/290402
                HOW TO: Remove the Service Pack Restore Files and Folders in
                Windows
  http://support.microsoft.com/kb/253597
                Automating Disk Cleanup Tool in Windows

Schedule Tasks in Windows.
==========================

List registered of task.
------------------------
::

  $ schtasks /query

Create task.
------------
::

  $ schtasks /create /tn %TASK_NAME% /ru %ROOT% /sc daily /st 23:00:00 /tr "rundll32.exe user32.dll,LockWorkStation"

/sc can be one of::

  MINUTE HOURLY DAILY WEEKLY MONTHLY ONCE ONSTART ONLOGON ONIDLE

Delete task.
------------
::

  schtasks /delete /tn %TASK_NAME% /f

Change NTFS permission.
=======================

  http://support.microsoft.com/kb/919240
                The Icacls.exe utility is available for Windows Server 2003 with
                Service Pack 2

Change NTFS permission with 'icacls'.
-------------------------------------

'icacls' allow option:

 * /c - Continues the operation despite any file errors. Error messages will
   still be displayed.
 * /t - Performs the operation on all specified files in the current directory
   and its subdirectories.
 * /l - Performs the operation on a symbolic link versus its destination.
 * /q - Suppresses success messages.

Recursively change the owner of all matching files to the specified user::

  cmd> icacls %dir% /setowner %user% /t /c

or simply::

  cmd> takeown /r /f %file%

Recursively grand full access for everyone::

  cmd> icacls %dir% /t /grant:r %user%:(f)
  cmd> icacls %dir% /t /grant:r *S-1-1-0:(f)

Well-known security identifiers (SID).
======================================

  S-1-0-0
                Null SID. A group with no members. This is often used when a SID
                value is not known.
  S-1-1-0
                World/Everyone. A group that includes all users.
  S-1-3-0
                Creator Owner ID. A security identifier to be replaced by the
                security identifier of the user who created a new object. This
                SID is used in inheritable ACEs.
  S-1-3-1
                Creator Group ID. A security identifier to be replaced by the
                primary-group SID of the user who created a new object. Use this
                SID in inheritable ACEs.
  S-1-5-6
                Service. A group that includes all security principals that have
                logged on as a service. Membership is controlled by the
                operating system.
  S-1-5-7
                Anonymous. A group that includes all users that have logged on
                anonymously. Membership is controlled by the operating system.
  S-1-5-32-544
                Administrators group.
  S-1-5-32-545
                Users group.
  S-1-5-32-546
                Guests. By default, the only member is the Guest account. The
                Guests group allows occasional or one-time users to log on with
                limited privileges to a computer's built-in Guest account.
  S-1-5-32-547
                Power Users. Power users can create local users and groups;
                modify and delete accounts that they have created; and remove
                users from the Power Users, Users, and Guests groups. Power
                users also can install programs; create, manage, and delete
                local printers; and create and delete file shares.

  http://msdn.microsoft.com/en-us/library/aa379649.aspx
                Well-known SIDs
  http://support.microsoft.com/kb/243330
                Хорошо известные идентификаторы безопасности в операционных
                системах Windows
  http://en.wikipedia.org/wiki/Security_Identifier
                Security Identifier

Converting SID to names and inside out.
=======================================

Use 'PsGetSid' utility from Sysinternals::

  cmd> PsGetSid S-1-3-0
  cmd> PsGetSid "\NULL SID"

Gathering info about Windows.
=============================
::

  cmd> systeminfo

From ``Win+R``::

  helpctr.exe -mode hcp://system/sysinfo/msinfo.xml

or by::

  cmd> %SystemRoot%\pchealth\helpctr\binaries\helpctr.exe -mode hcp://system/sysinfo/msinfo.xml

Automatically logon to Windows.
===============================
::

  cmd# control userpasswords2

Format drive.
=============

Replace with own disk letter::

  cmd# format E: /q /fs:ntfs

See:

  http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/format.mspx
                Formats the disk in the specified volume to accept Windows
                files.

