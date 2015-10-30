.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

=======
 Xorg.
=======
.. contents::

Where find info?
================
::

  $ man 5 xorg.cong

Enable Ctrl+Alt+Backspace.
==========================
::

  $ cat /etc/X11/xorg.conf
  ...
  Section "ServerFlags"
        Option      "DontZap" "false"
  EndSection

How set standby time?
=====================

Put something like this in xorg.cong::

  Section "ServerFlags"
      # Disallows the use of the Ctrl+Alt+Keypad-Plus and Ctrl+Alt+Keypad-Minus.
      Option "DontZoom"       "true"
      # Blank phase of the screensaver.
      #Option "BlankTime"      "0"
      # Standby phase of DPMS mode.
      Option "StandbyTime"     "10"
      #
      #Option "SuspendTime"    "0"
      #
      #Option "OffTime"        "0"
  EndSection

Time measure in minute.

To enable this configuration you must set "DPMS" option in "Monitor" section::

  Section "Monitor"
  ...
      Option "DPMS"
  ...
  EndSection

To view current DPMS settings::

  $ xset q

To disable DPMS for current session use command::

  $ xset -dpms

To turn off monitor use::

  $ sleep 1; xset dpms force off

See:

 * https://wiki.archlinux.org/index.php/Display_Power_Management_Signaling

Set display dimensions.
=======================

To see currect settings type::

  $ xdpyinfo | grep   dimensions:
  dimensions:    1280x1024 pixels (382x302 millimeters)

From this dimensions calculated your display dpi resolution::

  $ xdpyinfo | grep resolution:
  resolution:    85x86 dots per inch

To set dimensions edit '/etc/X11/xorg.conf' (size in mm)::

  $ cat /etc/X11/xorg.conf
  ...
  Section "Monitor"
  ...
    DisplaySize     width height
  ...
  EndSection

Overriding EDID Settings for NVidia cards.
------------------------------------------

If you're using NVIDIA display drivers version 8756 or above and your monitor
reports an EDID DPI value, you must tell the drivers to ignore this value as
it takes precedence over all the above configuration options/arguments::

  Section "Monitor"
  ...
    DisplaySize     width height
    Option         "UseEdidDpi"  "false"
  ...
  EndSection

