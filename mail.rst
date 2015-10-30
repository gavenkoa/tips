.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 Mail.
=======
.. contents::

Message headers fields.
=======================
::

  from            =       "From:" mailbox-list CRLF
  sender          =       "Sender:" mailbox CRLF
  reply-to        =       "Reply-To:" address-list CRLF

  to              =       "To:" address-list CRLF
  cc              =       "Cc:" address-list CRLF
  bcc             =       "Bcc:" (address-list / [CFWS]) CRLF
  newsgroups

  http://tools.ietf.org/rfc//rfc2076.txt
                Common Internet Message Headers, Informational
  http://tools.ietf.org/rfc/rfc2822.txt
                Internet Message Format, Standard Track
  http://tools.ietf.org/rfc/rfc2821.txt
                Simple Mail Transfer Protocol, Standard Track

Sending mail with ssmtp.
========================
::

  $ cat /etc/ssmtp/ssmtp.conf
  Mailhub=smtp.gmail.com:587
  FromLineOverride=YES
  UseSTARTTLS=yes
  AuthUser=gavenkoa
  AuthPass=XXXXXX

Sending email via gmail in emacs.
=================================
::

  ; install starttls from here (no need for patch)
  ; http://josefsson.org/emacs-smtp-starttls.html

  (setq send-mail-function 'smtpmail-send-it
     message-send-mail-function 'smtpmail-send-it
     smtpmail-starttls-credentials
     '(("smtp.gmail.com" 587 nil nil))
     smtpmail-auth-credentials
     (expand-file-name "~/.authinfo")
     smtpmail-default-smtp-server "smtp.gmail.com"
     smtpmail-smtp-server "smtp.gmail.com"
     smtpmail-smtp-service 587
     smtpmail-debug-info t
     starttls-extra-arguments nil
     smtpmail-warn-about-unknown-extensions t
     starttls-use-gnutls nil)

Update ``~/..authinfo``::

  machine smtp.gmail.com login [your name]@gmail.com password [your password]

And finally download, unzip, make and install startttls::

  http://josefsson.org/emacs-smtp-starttls.html

 * http://justinsboringpage.blogspot.com/2009/02/sending-email-via-gmail-in-emacs.html
 * http://obfuscatedcode.wordpress.com/2007/04/26/configuring-emacs-for-gmails-smtp

Mail etiquette.
===============

Bottom vs. top quoting.
-----------------------

Just not use top quoting!

Stallman warn about Google.
---------------------------

  http://www.mail-archive.com/gnu-emacs-sources@gnu.org/msg00302.html

Storage format for email.
=========================

mbox.
-----

  http://tools.ietf.org/html/rfc4155
                The application/mbox Media Type (Category: Informational)
  http://en.wikipedia.org/wiki/Mbox
                Mbox at Wikipedia.

maildir.
--------

  http://en.wikipedia.org/wiki/Maildir

MH mailbox format.
------------------

  http://en.wikipedia.org/wiki/MH_Message_Handling_System

