.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

================
 Java language.
================
.. contents::

Class version.
==============

  =========  ====== =====================
  major      minor  Java platform version
  =========  ====== =====================
  45 0x27    3      1.0
  45 0x27    3      1.1
  46 0x28    0      1.2
  47 0x29    0      1.3
  48 0x30    0      1.4
  49 0x31    0      5.0
  50 0x32    0      6.0
  51 0x33    0      7
  52 0x34    0      8
  =========  ====== =====================

where ``minor`` and ``major`` are value of 6 and 8 bytes in .class file::

  0xCA, 0xFE, 0xBA, 0xBE, 0x00, minor, 0x00, major

Access modifiers.
=================

Public.
-------

 * Public class is visible in other packages.
 * Public field is visible everywhere (class must be public too).

Private.
--------

 * Private variables or methods may be used only by an instance of the same
   class that declares the variable or method
 * A private feature may only be accessed by the class that owns the feature.

Protected.
----------

 * Is available to all classes in the same package and also available to all
   subclasses of the class that owns the protected feature.
 * This access is provided even to subclasses that reside in a different
   package from the class that owns the protected feature.

default.
--------

What you get by default ie, without any access modifier.

 * It means that it is visible to all within a particular package.

static.
-------

 * Static means one per class, not one for each object no matter how many
   instance of a class might exist. This means that you can use them without
   creating an instance of a class.
 * Static methods are implicitly final, because overriding is done based on
   the type of the object, and static methods are attached to a class, not an
   object.
 * A static method in a superclass can be shadowed by another static method in
   a subclass, as long as the original method was not declared final.
 * You can't override a static method with a nonstatic method.

final.
------

 * A final class can't be extended ie., final class may not be subclassed.
 * A final method can't be overridden when its class is inherited.
 * You can't change value of a final variable.

Exceptions.
===========

A checked exception is some subclass of Exception (or Exception itself),
excluding class RuntimeException and its subclasses.

Unchecked exceptions are RuntimeException and any of its subclasses. Class
Error and its subclasses also are unchecked. With an unchecked exception,
however, the compiler doesn't force client programmers either to catch the
exception or declare it in a throws clause.

Inner classes.
==============

Nested top-level classes.
-------------------------

If you declare a class within a class and specify the static modifier, the
compiler treats the class just like any other top-level class.

Any class outside the declaring class accesses the nested class with the
declaring class name acting similarly to a package. eg, outer.inner. Top-level
inner classes implicitly have access only to static variables. There can also
be inner interfaces. All of these are of the nested top-level variety.

Member classes.
---------------

Member inner classes are just like other member methods and member variables
and access to the member class is restricted, just like methods and variables.
This means a public member class acts similarly to a nested top-level class.

The primary difference between member classes and nested top-level classes is
that member classes have access to the specific instance of the enclosing
class.

Local classes.
--------------

Local classes are like local variables, specific to a block of code. Their
visibility is only within the block of their declaration. In order for the
class to be useful beyond the declaration block, it would need to implement a
more publicly available interface.

Because local classes are not members, the modifiers public, protected,
private, and static are not usable.

Anonymous classes.
------------------

Anonymous inner classes extend local inner classes one level further. As
anonymous classes have no name, you cannot provide a constructor.

64-bit problem.
===============

  http://www.java.com/en/download/faq/java_win64bit.xml
                Which version of Java should I download for my 64-bit Windows
                operating system?
  http://java.sun.com/javase/6/webnotes/install/system-configurations.html
                Java SE 6 Release Notes Supported System Configurations

Java performance.
=================

  http://java.sun.com/performance/reference/whitepapers/5.0_performance.html
  http://java.sun.com/performance/reference/whitepapers/6_performance.html

Creating jar.
=============
::

  $ jar cf myFile.jar *.class
  $ jar cmf myManifestFile myFile.jar *.class
  $ jar -cfe Main.jar foo.Main foo/Main.class

Profiling Java.
===============
::

  $ java -Xprof com.vendor.product.Clazz
  $ java -Xrunhprof:help

Debugging Java.
===============

Compile with ``-g`` to preserve source code information::

  $ javac -g -cp $CLASSPATH -sourcepath $SRC_DIR -d $BUILD_DIR

To run Java program in debugger::

  $ jdb -cp $CLASSPATH -sourcepath $SRC_DIR

To attach to Java application you firstly must run application with (use
``dt_shmem`` for Windows and ``dt_socket`` for Linux)::

  $ java -Xdebug -Xrunjdwp:transport=dt_shmem,server=y,suspend=n,address=$PORT \
    com.vendor.product.Clazz

and then attach with debugger::

  $ jdb -attach $PORT

Dump current thread traces and memory statistic to stdout::

  $ kill -QUIT $PID

Debug class loading.
====================

To dump class loading and unloading to ``System.out`` add to ``java`` opts::

  $ java -XX:+TraceClassLoading -XX:+TraceClassUnloading ...
  $ java -verbose:class ...

To review loaded classes explore heap dump in ``visualvm`` (visit "Classes"
tab).

Decompile class file.
=====================
::

  $ javap -v -p -c My.java

Find jar by class.
==================

  http://mvnrepository.com/search.html?query=PKG
  http://www.jarfinder.com

Set default Java in Debian.
===========================
::

  $ update-java-alternatives -l
  $ sudo update-java-alternatives -s java-1.8.0-openjdk-i386

or individually for each executable::

  $ sudo update-alternatives --config java

Import SSL certificate.
=======================

Get cert with::

  $ openssl s_client -connect promin-test.it.loc:433

  -----BEGIN CERTIFICATE-----
  ...
  -----END CERTIFICATE-----

or by opening URL in broswer and exporting in "Page info" ==> "Security" menu.

Call import utility with default ``changeit`` password::

  $ keytool -importcert -file $YOUR.crt -keystore $JAVA_HOME/jre/lib/security/cacert -alias $ANY -storepass changeit
  $ keytool -list -v -keystore $JAVA_HOME/jre/lib/security/cacert -storepass changeit

Import certificate system wide in Debian by (note, ``.crt`` extention is
mandatory)::

  $ sudo mkdir /usr/share/ca-certificates/$ANY/    # don't mess with other certs
  $ sudo cp /tmp/$YOUR.crt /usr/share/ca-certificates/$ANY/
  $ sudo dpkg-reconfigure --force ca-certificates  # check your cert in curses GUI!
  $ sudo update-ca-certificates --fresh --verbose

Java EE versions.
=================

======= ======== ======== ========
Java EE Servlet  JSP      JSTL
======= ======== ======== ========
6       3.0      2.2      -
5       2.5      2.1      1.2
1.4     2.4      2.0      1.1
1.2     2.3      1.2      1.0
======= ======== ======== ========

To set servlet version check ``WEB-INF/web.xml``::

  <web-app xmlns="http://java.sun.com/xml/ns/javaee" version="3.0">

See:

  http://jcp.org/aboutJava/communityprocess/final/jsr315/index.html
                Servlet 3.0 Specification
  http://jcp.org/aboutJava/communityprocess/mrel/jsr154/index.html
                Servlet 2.5 Specification
  http://www.mularien.com/blog/2008/04/24/how-to-reference-and-use-jstl-in-your-web-application/
                How to Reference and Use JSTL in your Web Application
  http://en.wikipedia.org/wiki/Java_EE_version_history
                Java EE version history

Java interactive shell.
=======================

Just use Groovy. ``bsh`` is older alternative without code completion.
