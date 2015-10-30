.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=========
 Django.
=========
.. contents::

Hello world Django app.
=======================
::

  $ cd ~/devel
  $ django-admin.py startproject dj
  $ cd dj
  $ django-admin.py startapp hello
  $ cat >hello/views.py <<EOF
  from django.http import HttpResponse
  def hello(request):
      return HttpResponse("Hello world")
  EOF
  $ cat >urls.py <<EOF
  from django.conf.urls.defaults import patterns, include, url
  from hello.views import hello
  urlpatterns = patterns(
      '',
      url(r'^hello/$', hello),
  )
  EOF
  $ ./manage.py runserver

Start server.
=============

  $ ./manage.py runserver
  $ ./manage.py runserver 8080
