.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 JBoss AS.
===========
.. contents::

JBoss documentation.
====================

 * https://docs.jboss.org/author/display/AS7/Documentation
 * https://docs.jboss.org/author/display/AS7/Getting+Started+Guide
 * https://docs.jboss.org/author/display/AS7/Management+Clients
 * https://community.jboss.org/wiki/UsingJconsoleToConnectToJMXOnAS7
 * https://community.jboss.org/wiki/UsingCLIGUIWithJconsoleOnJBossAS7

Starting local JBoss AS.
========================
::

  $ /opt/jboss/bin/standalone.sh &

Deploy war to JBoss AS with Maven.
==================================
::

  $ mvn help:describe -DartifactId=jboss-as-maven-plugin -DgroupId=org.jboss.as.plugins

See:

 * http://docs.jboss.org/jbossas/7/plugins/maven/latest/examples/deployment-example.html


