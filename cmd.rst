.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

====================
 CMD Windows shell.
====================
.. contents::

Quoting.
========

 * Arguments are delimited by white space, which is either a space or a tab.
 * A string surrounded by double quotation marks is interpreted as a single
   argument.
 * A double quotation mark preceded by a backslash, \", is interpreted as a
   literal double quotation mark.
 * Backslashes are interpreted literally, unless they immediately precede a
   double quotation mark.
 * If an even number of backslashes is followed by a double quotation mark,
   then one backslash (\) is placed in the argv array for every pair of
   backslashes (\\), and the double quotation mark (") is interpreted as a
   string delimiter.
 * If an odd number of backslashes is followed by a double quotation mark,
   then one backslash (\) is placed in the argv array for every pair of
   backslashes (\\) and the double quotation mark is interpreted as an escape
   sequence by the remaining backslash, causing a literal double quotation
   mark (") to be placed in argv.
 * In double quote mark need surround such chars::

     & < > [ ] { } ^ = ; ! ' + , ` ~ %

   Also all this char can be escaped by ^ char.
 * Long line can be truncated by ^ char, in this case trailing white spaces
   not allowed.
 * To quote percent sign % before alpha char in batch file double it
   occurrences or plase in quotes::

     prog '%'HOME'%' "%"HOME"%" %%HOME%

  http://msdn.microsoft.com/en-us/library/ms880421.aspx
                Parsing C Command-Line Arguments

Variables.
==========

Variable name start with letter and underscore, next chars can be letter,
number and underscore. Variable name is case insensitive.

List of variables.
------------------
::

  cmd> set
  ...
  VAR=VALUE

Getting.
--------

Write %VAR% in place where you want insert variable VAr value.

Setting.
--------
::

  cmd> set /p VAR=VALUE

Deleting.
---------
::

  cmd> set VAR=

Input from user.
----------------
::

  cmd> set /p VAR=PROMPT

VAR is variable name, PROMPT is displayed prompt.

Input from file.
----------------

  cmd> set /p VAR=<FILE

VAR is variable name, FILE is file name. Sfter executing VAR contain first
line from FILE.

CMD tricks.
===========
::

  $ set /p TOOLOUTPUT= < temp.txt

  $ for /f "tokens=*" %%i in ('%~dp0sometool.exe') do set TOOLOUTPUT=%%i

  $ for /f "tokens=1 delims=" %%s in (users.txt) do (echo %%S & command "%%S") >> outputfile.txt

Resize cmd window.
==================
::

  cmd# mode CON: COLS=120 LINES=40

Limits.
=======

Variable value and one line command string after expansion can not exceed 8191
characters for Windows XP and later and 2047 for Windows NT, Windows 2000.

  http://support.microsoft.com/default.aspx?scid=kb;en-us;830473
                Command prompt (Cmd. exe) command-line string limitation

How run cmd on 64-bit OS.
=========================

From 64-bit process::

  %windir%\System32\cmd.exe (for 64-bit)
  %windir%\SysWOW64\cmd.exe (for 32-bit)

From 32-bit process::

  %windir%\System32\cmd.exe (for 32-bit)
  %windir%\Sysnative\cmd.exe (for 64-bit)

  http://msdn.microsoft.com/en-us/library/aa384187%28VS.85%29.aspx
                File System Redirector

