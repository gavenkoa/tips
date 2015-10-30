.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 Firefox.
==========
.. contents::

How edit settings?
==================

Default settings stored in 'prefs.js'. If you don't want rewrite it
edit/create 'user.js'::

  $ emacs ~/.mozilla/firefox/xxxxxxx.default/user.js

or open link::

  about:config

See

  http://www.mozilla.org/unix/customizing.html#prefs

Profiles.
=========

How create new profile.
-----------------------

Close all opened firefox windows (File -> Exit)! And run::

  $ firefox -P

and in GUI push "Create profile" button and type profile name.

How to add old profile.
-----------------------

Locate profile config file::

  c:/Users/%USERNAME%/AppData/Roaming/Mozilla/Firefox/profiles.ini

and add entry::

  [Profile1]
  Name=test
  IsRelative=0
  Path=E:\home\.firefox

You must edit ``Profile1`` and ``Path`` lines.

How run two firefox simultaneously.
-----------------------------------
::

  $ firefox             # run firefox with default profile
  $ firefox -P second-profile-name -no-remote
  $ firefox -P third-profile-name -no-remote

How backup and restore profile.
-------------------------------

Just save content of '~/.mozilla/firefox/Profiles/xxxxxxx.default'.
To restore profile edit '~/.mozilla/firefox/profiles.ini'::

  [Profile<N>]
  Name=default
  IsRelative=1
  Path=Profiles/xxxxxxx.default
  Default=1

Change user agent.
==================

::

  general.useragent.override

For Debian Icewasel just remove ``Icewasel`` from user agent string. Example::

  Mozilla/5.0 (X11; Linux x86_64; rv:44.0) Firefox/44.0

How to prevent links from opening a new window?
===============================================

Go to about:config and set::

  browser.link.open_newwindow - 3. May be 1:cur 2:win 3:tab
  browser.link.open_external - 3. May be 1:cur 2:win 3:tab
  browser.link.open_newwindow.restriction - 0. May be 0, 1. 2

See also:

  http://kb.mozillazine.org/Browser.link.open_external
  http://kb.mozillazine.org/Browser.link.open_newwindow.restriction

How to prevent links from resize window?
========================================
::

  Preference -> Content -> JavaScript ->
                Advanced -> disable "Move and resize existing windows"

How limit simultaneously connection counts?
===========================================
::

  network.http.max-connections - 4

or search by word 'connections' in 'about:config'.

See:

  http://kb.mozillazine.org/Network.http.max-connections

Copy link without escaping non ASCII chars.
===========================================

Run about:config and set network.standard-url.escape-utf8 to false.

Firefox downloading.
====================

  ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/
                Download older version.

Privacy.
========

See

  http://www.mozilla.com/en-US/privacy-policy.html
  http://www.mozilla.com/en-US/legal/privacy/firefox-en.html

Do not send anything through Breakpad.
--------------------------------------

Breakpad is crash report library. If firefox crash Breakpad can send core file
to Mozilla.

The breakpad report server linked to in about:crashes (you can see which and
where report you send).

breakpad.reportURL is URL where send report. Set it to http://localhost to
not send report.

  http://kb.mozillazine.org/Breakpad.reportURL

Do not use "Report Broken Web Site Feature" and "Report Web Forgery Feature".
-----------------------------------------------------------------------------

This feature available through "Help" menu.

Be careful with "Automated Update Service".
-------------------------------------------

It can be disabled through "Tools -> Advanced -> Update".

Disable "Location-aware Feature".
---------------------------------

Beginning with Firefox 3.5, Firefox offers a Location-Aware Feature, parts of
which may be provided by third party service providers.

To disable Location-aware Feature set "geo.enabled" to "false".

Per site permission can accesssed through "Navigate to the site" -> "Tools"
menu -> "Page Info" -> "Permissions tab" -> "Share Location".

See

  http://www.mozilla.com/en-US/firefox/geolocation/

Disable Google safe browsing.
-----------------------------

It can be disabled through "Tools -> Options -> Security tab", untick the
checkboxes for attacks and forgeries.

Set

  browser.safebrowsing.enabled  "false"
                do not use safebrowsing
  browser.safebrowsing.malware.enabled "false"
                do not download malware blacklists and do not check downloads
  browser.safebrowsing.remoteLookups "false"
                use local blacklist to determine a site's phishiness instead
                submitting the URL to a third party (deprecated?)

See

  http://kb.mozillazine.org/Browser.safebrowsing.enabled
  http://kb.mozillazine.org/Browser.safebrowsing.remoteLookups

View_source.
============

  view_source.wrap_long_lines
                True - HTML code will wrap in the view source window, false
                (default).
  view_source.syntax_highlight
                True (default) - enable syntax highlighting in the view source
                window. "View → Syntax Highlighting".

Privacy.
========

  privacy.item.cache
                True (default) - clear the cache when using the Clear Private Data feature
                (Firefox 1.5 and above only). This can be changed via "Tools → Options →
                Privacy → Settings..." (Firefox 1.5) or "Tools → Options → Privacy /
                Private Data → Settings..." (Firefox 2.0 and above).
  privacy.item.cookies
                True - delete all cookies when using the Clear Private Data feature
                (Firefox 1.5 and above only).
                This can be changed via "Tools → Options → Privacy → Settings..." (Firefox
                1.5) or "Tools → Options → Privacy / Private Data → Settings..." (Firefox
                2.0 and above).
  privacy.item.downloads
                True (default) - clear history of downloaded files when using the Clear
                Private Data feature (Firefox 1.5 and above only).
                Note: This can be changed via "Tools → Options → Privacy → Settings..."
                (Firefox 1.5) or "Tools → Options → Privacy / Private Data → Settings..."
                (Firefox 2.0 and above).
  privacy.item.formdata
                True (default) - clear all saved form data when using the Clear Private
                Data feature (Firefox 1.5 and above only).
                This can be changed via "Tools → Options → Privacy → Settings..." (Firefox
                1.5) or "Tools → Options → Privacy / Private Data → Settings..." (Firefox
                2.0 and above).
  privacy.item.history
                True (default) - clear the browsing history when using the Clear Private
                Data feature (Firefox 1.5 and above only).
                This can be changed via "Tools → Options → Privacy → Settings..." (Firefox
                1.5) or "Tools → Options → Privacy / Private Data → Settings..." (Firefox
                2.0 and above).
  privacy.item.offlineApps
                True - clear the offline website data when using the Clear Private Data
                feature (Firefox 3 and above only).
                This can be changed via "Tools → Options → Privacy / Private Data → Settings...".
  privacy.item.passwords
                True - delete all saved passwords when using the Clear Private Data
                feature (Firefox 1.5 and above only).
                This can be changed via "Tools → Options → Privacy → Settings..." (Firefox
                1.5) or "Tools → Options → Privacy / Private Data → Settings..." (Firefox
                2.0 and above).
  privacy.item.sessions
                True (default) - clear all authenticated SSL sessions when using the Clear
                Private Data feature (Firefox 1.5 and above only).
                This can be changed via "Tools → Options → Privacy → Settings..." (Firefox
                1.5) or "Tools → Options → Privacy / Private Data → Settings..." (Firefox
                2.0 and above).
  privacy.popups.firstTime
                True (default) - the user has never hidden the popup blocker notification
                bar before, so show a dialog explaining the status bar icon.
                False - the user has been informed of the status bar icon.
  privacy.popups.policy
                Determines the popup blocker behavior. 1 - allow popups, 2 - reject popups.
                Seems to be deprecated in favor of dom.disable_open_during_load.
  privacy.popups.showBrowserMessage
                True (default) - display a message at the top of the browser window when a
                popup has been blocked.
                False - display a status bar icon to indicate when a popup has been blocked.
  privacy.sanitize.promptOnSanitize
                True (default) - prompt before performing the Clear Private Data operation
                (Firefox 1.5 and above only)
                In Firefox 1.5 and above, this can be changed via "Tools → Options → Privacy → Settings...".
  privacy.sanitize.sanitizeOnShutdown
                True: Perform the Clear Private Data operation when closing the browser
                (Firefox 1.5 and above only).
                Note: In Firefox 1.5 and above, this can be changed via "Tools → Options →
                Privacy → Settings..."

Security.
=========

  security.warn_entering_secure
                True (default) - display a dialog warning the user when
                entering a secure site from an insecure one.
  security.warn_entering_secure.show_once
                True (default) - Leave the "Alert me whenever..." box
                unchecked on the security warning dialog.
  security.warn_entering_weak
                True (default) - display a dialog warning the user when
                entering an insecure site from a secure one.
  security.warn_entering_weak.show_once
                True (default) - leave the "Alert me whenever..." box
                unchecked on the security warning dialog.
  security.warn_leaving_secure
                True (default) - display a dialog warning the user when leaving a secure site.
  security.warn_leaving_secure.show_once
                True (default) - leave the "Alert me whenever..." box
                unchecked on the security warning dialog.
  security.warn_submit_insecure
                True (default) - display a dialog warning the user when
                submitting a form to an insecure site.
  security.warn_submit_insecure.show_once
                True (default) - leave the "Alert me whenever..." box
                unchecked on the security warning dialog.
  security.warn_viewing_mixed
                True (default) - display a dialog warning the user when a page
                has both encrypted and non-encrypted content.
  security.warn_viewing_mixed.show_once
                True (default) - leave the "Alert me whenever..." box unchecked
                on the security warning dialog.
  security.xpconnect.plugin.unrestricted
                True (default) - allow scripting of plugins by untrusted scripts.

Signon.
=======

  signon.prefillForms
                True (default) - allows auto-filling of stored usernames and
                passwords on webpage forms.
  signon.rememberSignons
                True (default) - enable the Password Manager.

JavaScript.
===========

  javascript.enabled (Boolean).
                Set this to true should you desire support for JavaScript. The
                same as the Enable JavaScript option in the Content tab.
  dom.allow_scripts_to_close_windows (Boolean).
                Setting this to true specifies that any window may be closed
                and isn’t recommended. Entering false specifies that only
                windows opened by script can be closed via close().
  dom.disable_image_src_set (Boolean).
                This option determines whether JavaScript is allowed to change
                images. Set this to true to enable this feature and false to
                disable it (recommended).
  dom.disable_open_click_delay (Integer).
                This option specifies the amount of time, in milliseconds,
                that must be surpassed before a pop-up window created by
                JavaScript setInterval() or setTimeout() calls aren’t managed
                by current pop-up blocker settings. Beneath this threshold
                existing pop-up blocker settings are applied. Default is 1000 (1 second).
  dom.disable_open_during_load (Boolean).
                Set this to true to enable Firefox’s built-in pop-up blocker, which disables the loading of much pop-up content on sites – which will mostly be advertisements (it’s worth noting this is not perfect and will also disable many legitimate pop-ups). Should a pop-up be blocked in this way an information bar will appear at the top of the window, from which you can select what action to take. Setting this to false disables the pop-up blocker (Not recommended). Note – This is the same as the Block pop-up windows option in the Options menu, Content tab.

  dom.disable_window_flip (Boolean).
                This option controls whether JavaScript may be used to bring windows into the foreground/background via focus(). Setting this to true disables such actions, which won’t affect new pop-ups from loading in the foreground, though can force existing ones to remain in the background unless switched to manually. Set this to false to allow the script to determine what happens. Note – This is the same as the Raise or lower windows option in Advanced JavaScript Settings.

  dom.disable_window_move_resize (Boolean).
                This option controls whether JavaScript can be used to move &/or resize windows, whereby setting this to false enables scripts to do this. It would perhaps be best to set this to true, allowing only yourself to resize/move windows. Note – This is the same as the Move or resize existing windows option in Advanced JavaScript Settings.

  dom.disable_window_open_feature.close (Boolean).
                Set this to false to enable the use of scripting to hide the close button of windows, true forces the close button to always be displayed (recommended).

  dom.disable_window_open_feature.directories (Boolean).
                Set this to false to enable the use of scripting to hide the bookmarks toolbar, true prevents the bookmarks toolbar from being hidden in this way.

  dom.disable_window_open_feature.location (Boolean).
                Set this to false to enable the use of scripting to hide the Location (Address) bar, true prevents the Address bar from being hidden.

  dom.disable_window_open_feature.menubar (Boolean).
                Set this to false to enable the use of scripting to hide the Menu bar, true disables the hiding of the Menu bar.

  dom.disable_window_open_feature.minimizable (Boolean).
                Set this to false to enable the use of scripting to disable the minimizing of windows, true enables the minimizing of such windows (recommended).

  dom.disable_window_open_feature.resizable (Boolean).
                Set this to true to enable the use of scripting to hide the close button of windows, false forces the close button to always be displayed (recommended).

  dom.disable_window_open_feature.scrollbar (Boolean).
                Set this to false to enable the use of scripting to hide the Scroll bar in windows, true disables the hiding of the Scroll bar in windows.

  dom.disable_window_open_feature.status (Boolean).
                This option controls whether JavaScript can be used to hide the status bar, whereby setting this to false enables scripts to do this. Set this to true to force the status bar to be displayed at all times. Note – This is the same as the Hide the status bar option in Advanced JavaScript Settings.

  dom.disable_window_open_feature.titlebar (Boolean).
                Set this to false to enable the use of scripting to hide the Title bar of windows, true forces the Title bar to always be displayed.

  dom.disable_window_open_feature.toolbar (Boolean).
                Set this to false to enable the use of scripting to hide the Navigation toolbar, i.e. Back, Forward, etc. buttons, false prevents the hiding of the Navigation toolbar.

  dom.disable_window_status_change (Boolean).
                This option controls whether JavaScript can be used to display custom text in the status bar, e.g. moving the mouse over a hyperlink normally would display where the link points to, though a script could be used to display something else instead. Set this to false to allow such custom status bar text displayed, while true will disable this. Note – This is the same as the Change status bar text option in Advanced JavaScript Settings.

  dom.event.contextmenu.enabled (Boolean).
                This option controls whether JavaScript can be used to alter, or even disable the context menu, e.g. right clicking could be disabled on certain pages. Set this to true if you wish to allow sites to be able to do this, while false ensures scripts can’t be used to alter this functionality. Note – This is the same as the Disable or replace context menus option in Advanced JavaScript Settings.

  dom.max_script_run_time (Integer).
                This specifies the amount of time, in seconds, that a script
                in content may run before being prompted whether to continue
                running it or not (default 10). Setting to 0 allows scripts to
                run as long as required.
  dom.max_chrome_script_run_time (Integer).
                This specifies the amount the amount of time, in seconds, that
                a script with chrome privileges may run before being prompted
                whether to continue running it or not (default 20).
  dom.popup_maximum (Integer).
                This value specifies the maximum number of pop-up windows that
                may be open simultaneously (default 20).

See

  http://kb.mozillazine.org/Dom.max_script_run_time
  http://kb.mozillazine.org/Dom.max_chrome_script_run_time

Plugin.
=======

  plugin.default_plugin_disabled
                True (default) - when a plugin is needed, prompt the user.
                False - don't prompt the user to install needed plugins.
  plugin.expose_full_path
                True - in about:plugins and navigator.plugins, reveal the full path to
                plugin files.
                False (default) - show only the plugin filename

Download Manager.
=================

  browser.download.manager.flashCount
                Set to 0 to stop flashing Download Manager.
  browser.download.manager.showAlertOnComplete
                Set to false to top flashing alter on complete download.
  browser.download.manager.retention
                Clear immediately the download history:
                0 - upon successful download
                1 - when the Firefox browser closes
                2 - needs user to clear it manually (default)
  browser.download.manager.closeWhenDone
                Set to false to stop Firefox closing Download Manager when download is
                complete.
  browser.download.manager.scanWhenDone
                Set to false to stop scaning for viruses.

Search.
=======

OpenSearch.
-----------

  http://en.wikipedia.org/wiki/OpenSearch

Smart Keywords.
---------------

Right-click in the search box, and you should see the context menu item Add a Keyword for
this Search.

Useful user plugin.
===================

Adblock Plus.
-------------

Block from loading ads and banners.

  http://adblockplus.org/en/
                home page
  https://addons.mozilla.org/en-US/firefox/addon/4364
                official mozilla download place

NoScript.
---------

Add-on allows JavaScript, Java and Flash and other plugins to be executed only by trusted
web sites of your choice (e.g. your online bank), and provides the most powerful Anti-XSS
protection available in a browser.

  http://noscript.net/
                home page

Cookie Monster.
---------------

Cookie Monster provides proactive cookie management on a site or domain level basis.

  https://addons.mozilla.org/en-US/firefox/addon/4703
                home page

FlashGot.
---------

The best Firefox download manager integration.

  http://flashgot.net
                home page

DownloadHelper.
---------------

  http://www.downloadhelper.net
                home page

GreaseMonkey.
-------------

Allows you to customize the way a webpage displays using small bits of JavaScript.

  http://www.greasespot.net
                Home page.
  https://addons.mozilla.org/firefox/748
                Download page.
  https://greasyfork.org/scripts/1317-download-youtube-videos-as-mp4
                Download YouTube Videos as MP4.

How to disable GZIP compression in Firefox?
===========================================
::

  user_pref("network.http.accept-encoding", ""); // default - "gzip,deflate".

Restart the Firefox in Safe Mode.
=================================

Poorly designed or incompatible extensions can cause problems with your browser, including
make it crash, slow down page display, etc::

  $ firefox -safe-mode

Hot calc by Firefox.
====================

At URI type some thing like "javascript: 4+5"

Disable safe browsing.
======================
::

  user_pref("browser.safebrowsing.enabled", false);
  user_pref("browser.safebrowsing.malware.enabled", false);
  user_pref("services.sync.prefs.sync.browser.safebrowsing.enabled", false);
  user_pref("services.sync.prefs.sync.browser.safebrowsing.malware.enabled;false", false);

Disable geo location.
=====================
::

  user_pref("geo.enabled", false);

You can fake your location by JSON like::

  {"location":{"latitude":48.861426,2.338929,"longitude":2.338929, "accuracy":20.0}}

in file pointed by::

  user_pref("geo.wifi.uri", "file:///home/user/fake-geo.json");

