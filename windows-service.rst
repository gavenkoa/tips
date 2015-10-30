.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==================
 Windows service.
==================
.. contents::

About Windows services.
=======================

  http://www.coretechnologies.com/WindowsServices/FAQ.html
    Windows Services Frequently Asked Questions (FAQ).

List services.
==============

List of all running services::

  cmd> net start

List of all services::

  cmd> sc query

List of specific service::

  cmd> sc query NAME

GUI tool::

  cmd> services.msc

Start/stop service.
===================
::

  cmd> net start NAME
  cmd> sc start NAME

  cmd> net stop NAME
  cmd> sc stop NAME

  cmd> services.msc

Create service.
===============

In order to create service from any executable use ``srvany.exe`` from Windows
Resource Kits 2003 (take attention to spaces after ``=``)::

  cmd> sc create NAME binPath= "c:\Program Files\Windows Resource Kits\Tools\srvany.exe" ^
       type= own start= auto error= normal DisplayName= "NAME for services.msc"

Then pass what ``srvany.exe`` wrapper to do::

  cmd> reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\NAME\Parameters" ^
     /v "Application" ^
     /d "\"c:\Program Files\Java\jre7\bin\java.exe\" -cp c:\home\devel\service Main"

Above you see quoting syntax for spaces and quotes. Next start service with::

  cmd> sc start NAME

If you make error recheck your settings with::

  cmd> reg query "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\NAME" /s

Or remove service and make steps again::

  cmd> sc delete NAME

Visit GUI ``services.msc`` and check with ``procexp.exe`` that service actually
do job.

  http://www.microsoft.com/en-us/download/confirmation.aspx?id=17657
    Windows Server 2003 Resource Kit Tools download.
  http://stackoverflow.com/questions/3663331/creating-a-service-with-sc-exe-how-to-pass-in-context-parameters
    How to pass parameters to sc.exe runnable.
  https://support.microsoft.com/KB/137890
    How To Create a User-Defined Service (with Srvany.exe).
  http://technet.microsoft.com/en-us/library/cc990289.aspx
    Sc create help.
  http://support.microsoft.com/kb/251192
    How to create a Windows service by using Sc.exe

Delete service.
===============
::

  cmd> sc delete NAME

Service wrapper.
================

  http://en.wikipedia.org/wiki/Service_wrapper
    Service wrapper
  http://nssm.cc/
    NSSM - the Non-Sucking Service Manager
  http://sourceforge.net/projects/yajsw/
    Yet Another Java Service Wrapper
  https://github.com/kohsuke/winsw/
    A wrapper executable that can be used to host any executable as an Windows
    service
  http://code.google.com/p/simple-service-wrapper/
    Simple Windows Service Wrapper

