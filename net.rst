.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 Network.
==========
.. contents::

Network managers.
=================

Mainstream in Debian:

  ``connman``
    Intel Connection Manager daemon.
  ``network-manager``
    Network management framework (daemon and userspace tools).
  ``wicd``
    Wired and wireless network manager.

Misc:

  ``netctl``
    Come under ``systemd`` umbrella, absent in Debian.
  WiFi Radar
    Python scripts that lanches another applications.

Ukraine internet provider.
==========================

Utel.
-----

User - none, password - none, phone - ``*99***1#`` or ``*99#``.

Peoplenet.
----------

User and password you get by sending SMS message to ``920`` number. Phone ``#777``.

DNS to IP address.
==================
::

  $ nslookup example.com

IP to DNS address.
==================
::

  $ nslookup 192.168.1.1

NetBIOS to IP address.
======================

By nbtstat.exe command from MS you can print NetBIOS name cache with
name-to-IP address mappings::

  $ nbtstat -c
  $ nbtstat -a NETBIOSNAME

IP to NetBIOS address.
======================
::

  $ nbtstat -A xxx.xxx.xxx.xxx

List of NetBIOS name.
=====================
::

  $ nbtstat -r

List of open ports.
===================

List of open ports under Windows.
---------------------------------
::

  cmd> netstat        # with DNS name resolution, TCP only
  cmd> netstat -n     # without name resolution, TCP only
  cmd> netstat -a -n  # TCP and UDP
  cmd> netstat -s     # show IP, ICMP, TCP, and UDP statistics.

List of open ports under Linux.
-------------------------------

``-t`` tcp, ``-u`` udp, ``-l`` local, ``-p`` process::

  $ sudo netstat -tulp

or to use port number instead of protocol name::

  $ sudo netstat -tulpn

Which processes open port?
==========================

Windows
-------
::

  cmd> netstat -o     # show PID
  cmd> netstat -b     # show also cmd name
  cmd> netstat -b -v  # show all modules (.exe and .dll) with full path

Linux.
------
::

  $ sudo netstat -tulpn

or::

  $ sudo lsof -i

How disable IPv6?
=================

Debian kernel 2.6/Ubuntu ("official" method)/Fedora Core.
---------------------------------------------------------

Comment in /etc/modprobe.d/aliases "alias net-pf-10 ipv6" and add alias
"net-pf-10 off", "alias ipv6 off"::

  $ sudo emacs /etc/modprobe.d/aliases
  ...
  $ cat /etc/modprobe.d/aliases
  ...
  # alias net-pf-10 ipv6
  alias net-pf-10 off
  alias ipv6 off
  ...

Reboot or::

  $ sudo update-modules

Another way is adding to /etc/modprobe.d/blacklist.local lines::

  blacklist ipv6

You can safely wipe out any IPv6 reference in ``/etc/hosts`` and
``/etc/network/interfaces``.

  http://wiki.debian.org/DebianIPv6
                DebianIPv6

RHEL4/Centos4.
--------------

As for Debian, but ``/etc/modprobe.d/aliases`` has name ``/etc/modprobe.conf``.

KDE.
----
::

  $ cat /etc/environment
  ...
  KDE_NO_IPV6=true
  ...

Firefox.
--------

See ``about:config`` page, set ``network.dns.disableIPv6`` to ``true``.

Clear saved Windows networking passwords.
=========================================
::

  cmd> rundll32.exe keymgr.dll, KRShowKeyMgr
  cmd> control userpasswords2                 # another way

Proxy auto-config.
==================

  http://en.wikipedia.org/wiki/Proxy_auto-config
