.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 Android.
==========
.. contents::

Official docs.
==============

  http://developer.android.com/sdk/index.html
    Get the Android SDK
  http://developer.android.com/guide/index.html
    Introduction to Android
  https://android.googlesource.com/platform/system/core/+/master/init/readme.txt
    init.rd file syntax.

Package repositories.
=====================

  https://play.google.com/
    Google package repository.
  https://f-droid.org/
    Free software repository.

Link to package description page:

  https://play.google.com/store/apps/details?id=com.google.android.talk

Mods.
=====

  http://xda-university.com/
    How to mod.
  http://www.cyanogenmod.org/about
    CyanogenMod
  https://www.clockworkmod.com/
    ClockworkMod

Connect to Android via USB by adb.
==================================

Add ``udev`` rule for fix permission issues::

  $ cat /etc/udev/rules.d/90-android.rules

  # Standard Google device.
  SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", ATTR{idProduct}=="0c03", MODE="0666", GROUP="plugdev"
  # China N101 II
  SUBSYSTEM=="usb", ATTR{idVendor}=="2207", ATTR{idProduct}=="0010", MODE="0666", GROUP="plugdev"

Reload udev rules and re-plug device via USB::

  $ sudo service udev force-reload

See:

  http://developer.android.com/tools/device.html
    Setting up a Device for Development.

Recovery.
=========

To enter phone to recovery mode press ``VolumeDown``+``Power`` button or::

  adb reboot recovery

See:

  http://teamw.in/project/twrp2
    Custom recovery built.

ADB tips.
=========

List available devices::

  $ adb devices

Install application from ``.apk`` file::

  $ adb install -r /path/to/application.apk

List installed package names (with path to ``.apk`` files!)::

  $ adb shell 'pm list packages -f'

Uninstall application by its package name::

  $ adb uninstall PACKAGE_NAME

Disable/enable application::

  $ adb shell pm disable PACKAGE_NAME
  $ adb shell pm enable PACKAGE_NAME

List of disabled packages::

  $ adb shell pm list packages -d

List currently run activities::

  $ adb shell 'dumpsys activity'

Find activities from package::

  $ adb shell 'pm list packages -f'
  $ adb pull APK_FROM_LIST
  $ aapt dump badging APK_FILE

Start an activity::

  $ adb shell am start PACKAGE_NAME/ACTIVITY_IN_PACKAGE
  $ adb shell am start PACKAGE_NAME/FULLY_QUALIFIED_ACTIVITY

Start an activity with action filter::

  android# am start -a com.example.ACTION_NAME -n com.package.name/com.package.name.ActivityName

List of running processes::

  $ adb shell ps

or (supported arguments
``user,group,comm,args,pid,ppid,pgid,etime,nice,rgroup,ruser,time,tty,vsz,stat,rss``)::

  $ adb shell
  % ps -o pid,user,group,rss,vsz,args

To kill process::

  $ adb shell ps | grep $REGEX
  $ adb shell kill $PID

To stop application::

  $ adb shell am kill com.google.android.contacts
  $ adb shell am force-stop com.google.android.contacts

Take a screenshort::

  $ adb shell screencap -p | perl -pe 's/\x0D\x0A/\x0A/g' > screen.png

Power button::

  $ adb shell input keyevent 26

Unlock screen::

  $ adb shell input keyevent 82

Show system log::

  $ adb logcat
  $ adb logcat "*:W"

List partition.
===============

List partitions (with sizes)::

  android# cat /proc/partitions
  android# cat /proc/mtd

List mounted file systems::

  android# mount
  android# df

Controlling Android from PC.
============================

 * http://code.google.com/p/androidscreencast/
 * http://code.google.com/p/android-screen-monitor/
 * http://androidwebkey.com/

Show screencast from Android.
=============================

  http://droid-at-screen.ribomation.com/
                Easily show the screen of an Android device on a computer/laptop
                (PC, Mac, Linux, ...) and then project the desktop using a
                LCD-projector.
