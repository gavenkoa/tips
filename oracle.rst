.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==================
 Oracle database.
==================
.. contents::

Oracle database development environment.
========================================

  http://en.wikipedia.org/wiki/Oracle_SQL_Developer
                Integrated development environment (IDE) for working with
                SQL/PLSql in Oracle databases.
  http://en.wikipedia.org/wiki/SQL*Plus
                An Oracle database client that can run SQL and PL/SQL commands
                and display their results.
  http://en.wikipedia.org/wiki/Oracle_Forms
                Is a software product for creating screens that interact with an
                Oracle database. It has an IDE including an object navigator,
                property sheet and code editor that uses PL/SQL.
  http://en.wikipedia.org/wiki/Oracle_JDeveloper
                JDeveloper is a freeware IDE supplied by Oracle Corporation. It
                offers features for development in Java, XML, SQL and PL/SQL,
                HTML, JavaScript, BPEL and PHP.
  http://en.wikipedia.org/wiki/Oracle_Reports
                Oracle Reports is a tool for developing reports against data
                stored in an Oracle database.

Useful PL/SQL stub.
===================
::

  set serveroutput on;
  set autotrace on statistics;
  set timing on;

  declare
  begin
    null;
  end;
  /

Database info.
==============

List of users::

  select distinct(OWNER) from ALL_TABLES;

List of current user owned tables::

  select * from USER_TABLES;
  select TABLE_NAME from USER_TABLES;

List of tables by owner::

  select OWNER || '.' || TABLE_NAME from ALL_TABLES
    order by OWNER;

List of current user table sizes::

  select SEGMENT_NAME, SEGMENT_TYPE, sum(BYTES) from USER_EXTENTS
    group by SEGMENT_NAME, SEGMENT_TYPE order by sum(BYTES);

  select sum(BYTES) from USER_EXTENTS;

Tables indexes::

  select * from USER_INDEXES order by TABLE_NAME;

List of index sizes::

  select index_name, table_name, sum(user_extents.bytes) as bytes from user_indexes
    left outer join user_extents on user_extents.segment_name = table_name
    group by index_name, table_name
    order by table_name;

List of tables without primary keys::

  select OWNER || '.' || TABLE_NAME from ALL_TABLES
    where TABLE_NAME not in (
      select distinct TABLE_NAME from ALL_CONSTRAINTS where CONSTRAINT_TYPE = 'P'
    ) and OWNER in ('USER1', 'USER2')
    order by OWNER, TABLE_NAME;

List of currenct user constraints::

  select * from USER_CONSTRAINTS;

List of tablespaces::

  select distinct TABLESPACE_NAME from USER_TABLES;

List of current user permissions::

  select * from SESSION_PRIVS;

List of user permissions to tables::

  select * from ALL_TAB_PRIVS where TABLE_SCHEMA not like '%SYS' and TABLE_SCHEMA not like 'SYS%';

List of user privileges::

  select * from USER_SYS_PRIVS
  select * from USER_TAB_PRIVS
  select * from USER_ROLE_PRIVS

Profiling.
==========

Timing info about last queries::

  select LAST_LOAD_TIME, ELAPSED_TIME, MODULE, SQL_TEXT elasped from v$sql
    order by LAST_LOAD_TIME desc

Improved version of above code::

  column LAST_LOAD_TIME format a20;
  column TIME format a20;
  column MODULE format a10;
  column SQL_TEXT format a60;

  set autotrace off;
  set timing off;

  select * from (
    select LAST_LOAD_TIME, to_char(ELAPSED_TIME/1000, '999,999,999.000') || ' ms' as TIME, MODULE, SQL_TEXT from SYS."V_\$SQL"
      where SQL_TEXT like '%BATCH_BRANCHES%'
      order by LAST_LOAD_TIME desc
    ) where ROWNUM <= 5;

In SQL/Plus::

  SET TIMING ON;
  -- do stuff
  SET TIMING OFF;

or::

  set serveroutput on
  variable n number
  exec :n := dbms_utility.get_time;
  select ......
  exec dbms_output.put_line( (dbms_utility.get_time-:n)/100) || ' seconds....' );

See:

  http://docs.oracle.com/cd/B19306_01/server.102/b14237/dynviews_2113.htm
                $SQL lists statistics on shared SQL area without the GROUP BY
                clause.

Last table modification time.
=============================
::

  select max(scn_to_timestamp(ora_rowscn)) from TBL;

  select timestamp from all_tab_modifications where table_owner = 'OWNER';
  select timestamp from all_tab_modifications where table_name = 'TABLE';

List of Oracle Reserved Words.
==============================

 * http://docs.oracle.com/cd/B19306_01/em.102/b40103/app_oracle_reserved_words.htm

Adjust date format.
===================
::

  column parameter format a32;
  column value format a32;
  select parameter, value from v$nls_parameters;

  alter session set NLS_DATE_FORMAT = 'yyyy-mm-dd HH:MI:SS';
  alter session set NLS_TIMESTAMP_FORMAT = 'MI:SS.FF6';
  alter session set NLS_TIME_FORMAT = 'HH24:MI:SS.FF6';

  select sysdate from dual;

Working with SQL/Plus.
======================

Show error details::

  show errors;

Dump how exactly field stored::

  select dump(date '2009-08-07') from dual;

