.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 sudo.
=======
.. contents::

Stop sudo asking for password.
==============================
::

  username ALL =(ALL) NOPASSWD: ALL

or::

  @group ALL =(ALL) NOPASSWD: ALL

Change user/primary group for executed command.
===============================================
::

  $ sudo -u $user -g $group $command

To allow this plase in /etc/sudoers::

  username ALL =(ALL:ALL) NOPASSWD: ALL

