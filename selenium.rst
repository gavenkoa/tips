.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

===========
 Selenium.
===========
.. contents::

Official docs.
==============

  http://docs.seleniumhq.org/docs/
                TOC.
  http://docs.seleniumhq.org/docs/03_webdriver.jsp
                WebDriver
  https://code.google.com/p/selenium/w/list
                Docs on Wiki about drivers and browser support.

WebDriver.
----------

 * http://code.google.com/p/selenium/wiki/FirefoxDriver
 * http://code.google.com/p/selenium/wiki/InternetExplorerDriver
 * http://code.google.com/p/selenium/wiki/ChromeDriver
 * http://selendroid.io/mobileWeb.html - Android.
 * http://code.google.com/p/selenium/wiki/OperaDriver
 * http://htmlunit.sourceforge.net/ - HtmlUnit.
   http://code.google.com/p/selenium/wiki/HtmlUnitDriver

Tutorials.
==========

  http://selenium2.ru/docs.html
                Russian translation of official docs.

com.thoughtworks.selenium.Selenium locator syntax.
==================================================

 * http://release.seleniumhq.org/selenium-remote-control/0.9.2/doc/java/com/thoughtworks/selenium/Selenium.html
 * http://selenium-training.israelekpo.com/targeting-elements.txt

Hi-level wrappers.
==================

Selenide.
---------

  https://github.com/codeborne/selenide/wiki/Selenide-vs-Selenium
                git repo
  http://ru.selenide.org/quick-start.html
                russian home page

Graphene 2.
-----------

  https://docs.jboss.org/author/display/ARQGRA2/Home
                home page
  https://community.jboss.org/wiki/ArquillianGraphene2
                wiki page

Set language preferences.
=========================

For FirefoxDriver::

  FirefoxProfile profile = new FirefoxProfile();
  profile.setPreference( "intl.accept_languages", "no,en-us,en" ); 
  WebDriver driver = new FirefoxDriver(profile);

See:

 * http://code.google.com/p/selenium/wiki/TipsAndTricks

