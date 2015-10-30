.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Maven.
========
.. contents::

Maven tutorial.
===============

 * http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html
 * http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html

Maven FAQ.
==========

 * http://maven.apache.org/general.html

Maven plugins.
==============

 * http://maven.apache.org/plugins/

Maven config location.
======================

``~/.m2/settings.xml``.

Generate simple project.
========================
::

  $ mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

Debug Maven build.
==================

Run build with ``-X`` option for verbose logging.

Project directory layout.
=========================

  http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html
    Introduction to the Standard Directory Layout.

Search for maven artifact by Java package or class name.
========================================================

 * https://repository.sonatype.org/
 * http://search.maven.org/

Get help on Maven plug-in.
==========================
::

  $ mvn help:describe -DartifactId=maven-war-plugin -DgroupId=org.apache.maven.plugins
  $ mvn help:describe -Dcmd=dependency:resolve -Ddetail

  $ mvn dependency:tree
  $ mvn dependency:list
  $ mvn dependency:resolve
  $ mvn dependency:resolve-plugins

  $ mvn -X ...

Reason for inclusion or omitting dependencies::

  $ mvn dependency:tree -Dverbose=true

What actual code processed by Maven (dump Maven config)::

  $ mvn help:effective-settings
  $ mvn help:effective-pom

Force update of dependencies.
=============================

You can try redownload snapshots by::

  $ mvn -U compile

You can fix damaged local ``~/.m2`` with::

  $ mvn dependency:purge-local-repository

In order to perform really clean download::

  $ mvn -Dmaven.repo.local=$HOME/.my/other/repository clean install

Find newer library and plugin versions.
=======================================

Check commands from ``versions-maven-plugin``::

  $ mvn versions:display-dependency-updates
  $ mvn versions:display-plugin-updates

Run Java main from Maven.
=========================
::

  mvn exec:java -Dexec.mainClass="com.vineetmanohar.module.Main" -Dexec.args="arg0 arg1 arg2"

How to run single unit test?
============================

``test`` property substituded to ``**/${test}.java`` pattern and override any
include/exclude patterns::

  $ mvn test -Dtest=SeriousComponentTest

or mostly same::

  $ mvn test-compile surefire:test -Dtest=RunMe

How do I skip the tests during the default lifecycle?
=====================================================
::

  $ mvn -DskipTests package
  $ mvn -Dmaven.test.skip=true package

Download all external dependencies sources and javadocs.
========================================================
::

  mvn dependency:resolve -Dclassifier=javadoc
  mvn dependency:resolve -Dclassifier=sources

Deploy parent pom without building children.
============================================
::

  $ mvn -N deploy

Run Ant from Maven.
===================

 * https://support.sonatype.com/entries/20736282-executing-an-external-ant-script-in-a-maven-build
 * https://support.sonatype.com/entries/20723081-running-an-inline-ant-script-in-a-maven-build
 * https://support.sonatype.com/entries/20744068-writing-a-maven-plugin-with-ant

