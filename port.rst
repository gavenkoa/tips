.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===============
 Network port.
===============
.. contents::

Port forwarding.
================
::

  $ ssh -L 8888:www.linuxhorizon.ro:80 user@computer -N
  $ ssh -L 8888:www.linuxhorizon.ro:80 -L 110:mail.linuxhorizon.ro:110 \
    25:mail.linuxhorizon.ro:25 user@computer -N

The second example (see above) show you how to setup your ssh tunnel for web, pop3
and smtp. It is useful to recive/send your e-mails when you don't have direct access
to the mail server.

For the ASCII art and lynx browser fans here is illustrated the first example::

   +----------+<--port 22-->+----------+<--port 80-->o-----------+
   |SSH Client|-------------|ssh_server|-------------|   host    |
   +----------+             +----------+             o-----------+
  localhost:8888              computer      www.linuxhorizon.ro:80

Reverse SSH Tunneling.
======================

Have you ever wanted to ssh to your Linux box that sits behind NAT? Now you can
with reverse SSH tunneling. This document will show you step by step how to set
up reverse SSH tunneling. The reverse SSH tunneling should work fine with Unix
like systems.

Let's assume that Destination's IP is 192.168.20.55 (Linux box that you want to
access).

You want to access from Linux client with IP 138.47.99.99.
Destination (192.168.20.55) <- NAT <- Source (138.47.99.99)

SH from the destination to the source (with public ip) using command below::

  $ ssh -R 19999:localhost:22 sourceuser@138.47.99.99

port 19999 can be any unused port. Now you can SSH from source to destination
through SSH tuneling::

  $ ssh localhost -p 19999

3rd party servers can also access 192.168.20.55 through Destination
(138.47.99.99). Destination::

  (192.168.20.55) <- |NAT| <- Source (138.47.99.99) <- Bob's server

From Bob's server::

  $ ssh sourceuser@138.47.99.99

After the sucessful login to Source::

  $ ssh localhost -p 19999

The connection between destination and source must be alive at all time. Tip:
you may run a command (e.g. watch, top) on Destination to keep the connection
active.

Port listening.
===============

Connect to a server::

  $ nc hostname port

Be a server::

  $ nc -l -p port

Simple filetransfer.
====================

Serve a file::

  $ nc -l -p port < file

Receive a file::

  $ nc hostname port > file

Filesystem cloning.
===================

Serve the filesystem::

  $ tar cOPp --same-owner / | nc -l -p port

Receive the filesystem::

  $ nc -w3 hostname port | tar xPp

Disk cloning.
=============

Serve the disk image::

  $ dd if=/dev/hda | nc -l -p port

Receive the image::

  $ nc -w3 hostname port | dd of=/dev/hda

Encrypted, compressed and IP restricted filetransfer.
=====================================================

If combining encryption and compression, be sure to compress first then
encrypt when sending and reverse the order for receiving. Do not attempt to
encrypt then compress. Compression works by finding patterns which are
destroyed intentionally by the process of encryption. Also, though not
required, specifying the IP address of the host that will be transferring the
file is a good idea.

Serving a compresssed, encrypted file from 192.168.0.1 to 192.168.0.2::

  $ gzip -c < file | openssl aes-128-cbc -e -k thispassword | nc -l 192.168.0.2 12345

Receiving, decrypting and decompressing that file::

  $ nc 192.168.0.1 12345 | openssl aes-128-cbc -d -k thispassword | gunzip -c > file

Scan with nmap.
===============
::

  $ nmap HOSTNAME

Scan with netcat.
=================
::

  $ nc -v -w 2 -z hostname portrange
  $ nc -v -w 2 -z hostname portlisting

Where portrange is for example "10-20" to scan all ports between 10 and 20,
portlisting is for example 11,20,135 will scan these ports.

I just tried this on windows xp, and the comma separated list of ports does
NOT work. Instead, use space separated list. eg::

  cmd> nc.exe -vv -w 2 -z www.example.com 20-25 79 80 110 137-139 443

