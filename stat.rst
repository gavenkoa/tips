.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=========================
 OS resource statistics.
=========================
.. contents::

Process list.
=============

Linux.
------

View current user process::

  $ ps

View all running process::

  $ ps -e

View process commands::

  $ ps -e -o pid,cmd

Show processes with same substring in command::

  $ pgrep -f $SUBSTR
  $ pgrep -l -f $SUBSTR
  $ pgrep -a -f $SUBSTR

View detail process info::

  $ ps -f <id>

Kill process::

  $ kill -s $SIG $PID

Kill processes with same name::

  $ killall $NAME

Kill processes with same substring in command::

  $ pkill -f $SUBSTR

View processes interactively::

  $ htop

Use ``-w`` option for wide output. Use this option twice for unlimited width.

Run as another user::

  $ su - $user
  $ command

or::

  $ sudo -u <user> -i <command>

FreeBSD.
--------

View current user process::

  $ ps

View all running process::

  $ ps -ax

View detail process info::

  $ ps -j <id>
  $ ps -l <id>

Windows.
--------

View all running process::

  cmd> TaskList
  Process Name                 PID Session Name     #Session       Memory
  ========================= ====== ================ ======== ============
  System Idle Process            0 Console                 0        28 KB
  System                         4 Console                 0       236 KB
  smss.exe                     592 Console                 0       432 KB
  csrss.exe                    656 Console                 0     4 404 KB
  winlogon.exe                 680 Console                 0     2 792 KB
  services.exe                 724 Console                 0     3 260 KB

View processes interactively::

  cmd> taskmgr

Kill process (TODO with which Windows version come?)::

  cmd> tskill {<pid>|<name>}

  cmd> taskkill /IM notepad.exe
  cmd> taskkill /PID 827

Run as another user::

  $ runas /u: TODO XXX

CPU consumption.
================

Linux interactive.
------------------
::

  $ top
  $ dstat

Try press 's' (strace), 'l' (lsof), 'F5' (tree view) in::

  $ htop

  http://htop.sourceforge.net/
                home page

Linux static.
-------------
::

  $ ps -eo %cpu,pid,cmd --sort=%cpu

FreeBSD interactive.
--------------------
::

  $ top

Windows.
--------
::

  cmd> taskmgr

Solaris.
--------

Interactive::

  $ perfmeter

Static::

  $ prstat

  $ mpstat <num> <seconds>

See

  http://developers.sun.com/solaris/articles/prstat.html
                Topping top in Solaris 8 with prstat.

Memory consumption.
===================

Linux interactive.
------------------
::

  $ top
  $ dstat

Linux static.
-------------

Vitual and resident memory size per process::

  $ ps -eo vsz,rsz,pid,cmd --sort=vsz --width 3000

Swap size and usage::

  $ free -t
               total       used       free     shared    buffers     cached
  Mem:       1028732      91928     936804          0       5396      34936
  -/+ buffers/cache:      51596     977136
  Swap:      1048568          0    1048568
  Total:     2077300      91928    1985372

  $ vmstat
  procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
   r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
   0  0      0 936804   5460  34936    0    0    21     5  363   29  0  0 99  0

System memory distribution::

  $ cat /proc/meminfo
  $ cat /proc/iomem
  $ cat /proc/pagetypeinfo
  $ cat /proc/buddyinfo
  $ sudo cat /proc/slabinfo
  $ sudo slabtop

Shared memory segments::

  $ ipcs -m -p

Process memory map::

  $ pmap -x $PID
  $ pmap -XX $PID

FreeBSD interactive.
--------------------
::

  $ top

FreeBSD static.
---------------

Swap size::

  $ swapinfo
  $ pstat -s

Swap usage::

  $ vmstat

Solaris.
--------
::

  $ sar -g

  $ vmstat

  $ prstat -s size

  $ prstat -a

Windows.
--------
::

  cmd> taskmgr

and add colums TODO.

Power usage.
============
::

  $ sudo powertop

Network activity.
=================
::

  $ ping $IP
  $ traceroute $IP
  $ mtr $IP
  $ sudo bmon
  $ sudo iftop -i wlan0

How many packets come through interface (size/type/source/destination)::

  $ sudo apt-get install netdiag
  $ sudo trafshow

Network status.
===============
::

  $ ip link show
  $ sudo ethtool eth0

Open ports.
===========
::

  $ nmap $IP

Opened file by process.
=======================

Linux.
------
::

  $ lsof -p <pid>

FreeBSD.
--------
::

  $ fstat -p <pid>

Windows interactive.
--------------------

procexp.exe from Sysinternals.

Windows static.
---------------

handle.exe from Sysinternals::

  cmd> handle -p 1265
  C: File  (RW-)   C:\Program Files\Common Files\GTK\2.0\bin
  288: Section       \BaseNamedObjects\mmGlobalPnpInfo

Opened file by user.
====================

FreeBSD.
--------
::

  $ fstat -u <user>

Opened network connection by process.
=====================================

Linux.
------
::

  $ lsof -i[46][protocol][@{hostname|hostaddr}][:{service|port}]
  $ netstat -p -l | grep $PORT

where ``[46]`` - IPV4 or IPV6, ``protocol`` - tcp, udp.

::

  $ fuser $port/tcp

To kill precess by port number::

  $ fuser -k $port/tcp       # with SIGKILL
  $ fuser -k -15 $port/tcp   # with SIGTERM
  $ fuser -k -TERM $port/tcp # with SIGTERM

FreeBSD.
--------

TODO

Windows.
--------
::

'-o' show PID, '-a' show all connection::

  cmd> netstat -o -a
  Type Local addr   Remote addr        State         PID
  TCP  user:1154    localhost:1153     ESTABLISHED   1512
  TCP  user:5152    localhost:1052     CLOSE_WAIT    1524
  TCP  user:1036    services.int:5222  ESTABLISHED   1188

Locked file by process.
=======================

Linux.
------
::

  $ lsof <file>

FreeBSD.
--------

TODO

Solaris.
--------

TODO

Windows interactive.
--------------------

procexp.exe from Sysinternals.

Windows static.
---------------

handle.exe from Sysinternals::

  cmd> handle d:\home
  ispell.exe         pid: 244     784: D:\home\drivers\token_api\src
  Far.exe            pid: 432     10C: D:\home\drivers\token_api

