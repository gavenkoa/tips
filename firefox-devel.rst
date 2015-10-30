.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========================
 Develop with/of Firefox.
==========================
.. contents::

Useful Firefox add-ons for developers.
======================================

  https://addons.mozilla.org/en-US/firefox/collections/mozilla/webdeveloper/
                Plug-ins for Web-development.

Firebug.
--------

Firebug integrates with Firefox to put a wealth of development tools at your fingertips
while you browse. You can edit, debug, and monitor CSS, HTML, and JavaScript live in any
web page.

  http://getfirebug.com
                home page
  https://addons.mozilla.org/firefox/addon/1843
                download page

Live HTTP Headers.
------------------

 * First by adding a 'Headers' tab in 'View Page Info' of a web page.
 * Second by adding a tool in the 'Tools->Web Development' menu to be able to display http
   headers in real time (while pages are being downloaded from the Internet.
 * Third by letting you edit request headers and replay an URL (beta). Look for the Replay
   button in the live window!

This project may be of some help for the following:

 * Help debugging web application.
 * See which kind of web server the remote site is using.
 * See the cookies sent by remote site.

Alternatively you can use fiddler2 (only Windows as it written in .NET)

  http://livehttpheaders.mozdev.org/
                home page
  https://addons.mozilla.org/en-US/firefox/addon/3829/
                download page
  http://www.fiddler2.com/fiddler2/
                Web Debugging Proxy

Wappalyzer.
-----------

Reverse which libraries and frameworks used by page.

  https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/
                download page

Tamper Data.
------------

 * Use tamperdata to view and modify HTTP/HTTPS headers and post parameters.
 * Trace and time http response/requests.
 * Security test web applications by modifying POST parameters.

Based on code and incompotable with "Live HTTP Headers" extensions.

  http://tamperdata.mozdev.org/index.html
                home page
  https://addons.mozilla.org/en-US/firefox/addon/966/
                download page
  http://jimbojw.com/wiki/index.php?title=Tamper_Data
                Tamper Data tutorial.

Extension security.
===================

 * https://developer.mozilla.org/en/Security_best_practices_in_extensions

Debugging in Firefox.
=====================

For JavaScript::

  // Enables strict JavaScript warnings in the Error Console.
  user_pref("javascript.options.strict", true);
  // Logs errors in chrome files to the Error Console. Enable Components.utils.reportError().
  user_pref("javascript.options.showInConsole", true);
  // Disables the XUL cache so that changes to windows and dialogs do not require a restart.
  user_pref("nglayout.debug.disable_xul_cache", true);
  // Enables the use of the dump() statement to print to the standard console.
  user_pref("browser.dom.window.dump.enabled", true);
  // This enables to run JavaScript code snippets in the chrome context of the Scratchpad from the Tools menu.
  user_pref("devtools.chrome.enabled", true);
  // This will send more detailed information about installation and update problems to the Error Console.
  user_pref("extensions.logging.enabled", true);
  user_pref("dom.report_all_js_exceptions", true);
  // This adds a "Browser Debugger" entry to the "Web Developer" submenu of the "Tools" menu.
  // The Browser Debugger can be used to debug the JavaScript code of extensions.
  user_pref("devtools.debugger.remote-enabled", true);
  // Detect deprecated code use.
  user_pref("devtools.errorconsole.deprecation_warnings", true);

Examine ``devtool`` options in ``about:config`` with prefix ``devtools.``::

  user_pref("devtools.debugger.enabled", true);
  user_pref("devtools.debugger.pause-on-exceptions", true);
  user_pref("devtools.debugger.auto-pretty-print", true);

  user_pref("devtools.debugger.chrome-debugging-host", "localhost");
  user_pref("devtools.debugger.chrome-debugging-port", 6080);
  user_pref("devtools.debugger.ignore-caught-exceptions", true);
  user_pref("devtools.debugger.remote-enabled, true);
  user_pref("devtools.debugger.remote-host", "localhost");
  user_pref("devtools.debugger.remote-port", 6000);

See:

  https://developer.mozilla.org/en/Setting_up_extension_development_environment
                setting up profile, options and about developer plugin

Debugging JavaScript with Web Console.
--------------------------------------

Instead of "Error Console" (press Ctrl+Shift+J) use "Web Console" (press
Ctrl+Shift+K) in Firefox >=4.0::

  console.log("str");
  console.info("str is %s", "str");
  console.warn("this is %o", this);
  console.error("int: %i, float: %f, string: %s, object: %o", 2, .333, "str", this);

To see stack-trace use::

  console.trace();
  console.log(new Error().stack);

See:

 * https://developer.mozilla.org/en-US/docs/Web/API/console
 * https://developer.mozilla.org/en/Using_the_Web_Console
 * https://developer.mozilla.org/en-US/docs/Tools/Web_Console

Debugging JavaScript with Firebug.
----------------------------------

With Firebug you can use 'console.log(obj)' for logging. Also output can be grouped with
console.group("name") to start a new indentation block, and then console.groupEnd().

Same but with different coloring do 'console.debug', 'console.info', 'console.warn', and
'console.error' functions.

  http://getfirebug.com/logging
                logging
  http://getfirebug.com/wiki/index.php/Console_API
                Console API
  http://getfirebug.com/wiki/index.php/Command_Line
                Command Line
  http://getfirebug.com/wiki/index.php/Console_Panel
                Console Panel

dump().
-------

Set in ``about:config`` ``browser.dom.window.dump.enabled`` to ``true``.

All messages go to native console. On Windows this require ``-console`` option
for ``firefox.exe``.

  https://developer.mozilla.org/en/DOM/window.dump

Components.utils.reportError.
-----------------------------

Write error msg to Error console (not in Web Console)::

  Components.utils.reportError("msg");
  // Show the error console.
  toJavaScriptConsole();

Firefox 3.x require set preference 'javascript.options.showInConsole' to 'true'
which is default value fro Firefox 4.x.

 * https://developer.mozilla.org/en/Components.utils.reportError

Build Firefox from sources.
===========================

  https://developer.mozilla.org/en/Build_Documentation
                Build Instructions
  https://developer.mozilla.org/en/Mozilla_Source_Code_%28Mercurial%29
                Getting Mozilla Source Code Using Mercurial

Native Firefox debugging.
=========================

 * https://developer.mozilla.org/en/how_to_get_a_stacktrace_with_windbg

Adding symbols from Symbol Server.
----------------------------------

Execute in WinDbg::

  .sympath SRV*c:\symcache\*http://msdl.microsoft.com/download/symbols;SRV*c:\symcache\*http://symbols.mozilla.org/firefox

or Ctrl+S and add::

  SRV*c:\symcache\*http://msdl.microsoft.com/download/symbols;SRV*c:\symcache\*http://symbols.mozilla.org/firefox

See:

  https://developer.mozilla.org/en/Using_the_Mozilla_symbol_server
