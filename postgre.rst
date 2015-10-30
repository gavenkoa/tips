.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 Postgre.
==========
.. contents::

Installing on Debian.
=====================

Install and create new user and database::

  $ sudo apt-get install postgresql postgresql-client
  $ sudo su - postgres
  % psql
  postgres=# CREATE USER "mypguser" WITH PASSWORD 'mypguserpass';
  postgres=# CREATE DATABASE "mypgdatabase" OWNER "mypguser";
  postgres=# \q

Connect as user ``mypguser`` to new database::

  $ su - mypguser
  $ psql mypgdatabase

In order to create local host superuser::

  $ sudo su - postgres
  $ createuser --superuser USER
  $ exit
  $ sudo -u USER psql

..

  https://wiki.debian.org/PostgreSql
    Debian wiki instructions.

List databases, schemas and tables.
===================================

Default database is ``postgres``.

To list databases and database locales::

  $ psql -U pgadmin -l

or::

  => SELECT datname FROM pg_database WHERE datistemplate = false;
  => \l

To switch databases::

  => \connect NAME

Schemas::

  => select schema_name from information_schema.schemata;
  => select nspname from pg_catalog.pg_namespace;
  => \dn *

To list all tables in the current database::

  => SELECT table_schema,table_name FROM information_schema.tables ORDER BY table_schema,table_name;
  => \dt

Set default schema.
===================
::

  set search_path to NAME;

Database, table, index size.
============================

Database size::

  SELECT pg_database_size('geekdb');  -- in bytes
  SELECT pg_size_pretty(pg_database_size('dbname'));

List of databases sizes::

  \l+

List tables sizes::

  \d+

Table total size (with indexes)::

  SELECT pg_size_pretty(pg_total_relation_size('schemaname.tablename'));

Sole table size (without indexes and other)::

  SELECT pg_size_pretty(pg_relation_size('schemaname.tablename'));

Largest table in the PostgreSQL database::

  SELECT relname, relpages FROM pg_class ORDER BY relpages DESC;

Using psql client.
==================

Using password file ``~/.pgpass``::

  # comment
  hostname:port:database:username:password
  hostname:port:*:username:password
  hostname:*:*:username:password

Connect by::

  $ psql -U $USER -h $HOST  $SCHEMA

How to view execution plan::

  EXPLAIN query;
  EXPLAIN ANALYZE query;

How to redirect the output of query to a file::

  \o output_file
  SELECT * FROM pg_class;

