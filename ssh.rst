.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 SSH/sshd.
===========
.. contents::

Debugging ssh client.
=====================
::

  $ ssh -vvv ...

Maintaining key pair.
=====================
::

  $ ssh-keygen -t dsa     # for DSA
  $ ssh-keygen -t rsa     # for RSA
  $ ssh-keygen -t dsa -C comment     # put own comment instead user@host
  $ ssh-keygen -t dsa -f my_dsa_key  # store priv key under my_dsa_key
                                     # and pub key under my_dsa_key.pub

  $ ssh-keygen -y -f ~/.ssh/id_dsa >~/.ssh/id_dsa.pub  # recover pub key from priv

  $ ssh-keygen -p -N "newphrase" -P "oldphrase" -f ~/.ssh/id_dsa
                                     # change passphrase of priv key

  $ ssh $user@$host cat ">>" "~/.ssh/authorized_keys" <~/.ssh/id_rsa.pub
                                     # public pub key on remote host

  $ ssh-copy-id  $user@$host         # alternative to previous command

Shell login.
============
::

  $ ssh $user@$host
  $ ssh $user@$host:$port

  $ ssh -i ~/.ssh/my_dsa_key $user@$host

or::

  $ ssh -l $user $host
  $ ssh -l $user $host:$port

X11 forwarding.
===============

Enable X11 forwarding on remote host in ``~/.ssh/config`` or ``/etc/ssh_config``::

  X11Forwarding yes

then login to this host by::

  $ ssh -X $user@$host

or by using trusted X11 forwarding::

  $ ssh -Y $user@$host

See:

  http://x.cygwin.com/docs/faq/cygwin-x-faq.html#q-ssh-no-x11forwarding
                X11Forwarding does not work with OpenSSH under Cygwin

Multiply private keys.
======================

ssh try use all listen keys::

  $ ssh -i ./priv1 -i ./priv2 $user@$host

or place in ~/.ssh/config::

  Host *
  IdentityFile ~/.ssh/identity # standard search path for protocol ver. 1
  IdentityFile ~/.ssh/id_dsa   # standard search path for RSA key protocol ver. 2
  IdentityFile ~/.ssh/id_rsa   # standard search path for DSA key protocol ver. 2
  IdentityFile ~/.ssh/my_dsa
  IdentityFile ~/.ssh/another_dsa

or per host private key::

  Host host1                   # alias, that user provide at CLI
  HostName host1.example.com   # real host name to log into
  User iam
  IdentifyFile ~/.ssh/iam_priv_dsa
  Host host2                   # alias, that user provide at CLI
  HostName 192.168.1.2         # real host IP to log into
  User admin
  IdentifyFile ~/.ssh/admin_priv_dsa

Installing sshd on Cygwin.
==========================

 * Install base packages and openssh.
 * Set CYGWIN env var to 'binmode ntsec'.
 * Create Windows user.
 * Recreate /etc/passwd::
     $ mkpasswd -l -u user >>/etc/passwd
   or::
     $ mkpasswd -l >/etc/passwd

  * Register sshd::
     $ mkdir -p /home/user
     $ ssh-host-config -y
  * Start::
     $ net start sshd
    or::
     $ cygrunsrv -S sshd

 * Check from remote host::
     $ ssh $gygwin_host -l user

To stop service use::

  $ net stop sshd
  $ cygrunsrv -E sshd

If you have ``connection closed`` error check permission for ``/home/*/.ssh``
directories. If you start service from ``user`` account - add write permission
to ``/home/*/.ssh``. I fix by::

  $ rm -r /home/*/.ssh
  cmd> icacls c:\opt\cygwin\home /t /grant:r cyg_server:(f)

Запускаем SSH server на правах произвольного пользователя.
----------------------------------------------------------

 * Создаем пользователя, например с именем user, задаем ему пароль, права (т.е.
   в какие группы будет входить) и т.д., пользователя не блокируем.
 * В консоле MMC добавляем оснастку "Параметры безопасности". Модифицируем
   параметры:

     "Параметры безопасности" --> "Локальные политики" --> "Назначение прав
     пользователя." --> "Вход в качестве службы" --> добавить 'user'.

     "Параметры безопасности" --> "Локальные политики" --> "Назначение прав
     пользователя" --> "Отклонить локальный вход" --> удалить 'user' (если был
     установлен).

     XXX "Принудительное удаленное завершение."

