.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Audio.
========
.. contents::

Sound in Debian.
================

 * http://wiki.debian.org/ALSA
 * http://wiki.debian.org/SoundFAQ

Test speaker and microphone.
============================

To configure audio devices::

  $ alsamixer
  $ pavucontrol

To hier voice from mic in speaker::

  $ arecord | aplay
  $ arecord -f cd | aplay -f cd

To list of available devices::

  $ aplay -l
  $ aplay -L
  $ arecord -l
  $ arecord -L

  $ pactl list

Play simple sounds.
===================
::

  $ sudo apt-get install sox
  $ play -n synth sin 440 vol -40dB
  $ play -n synth 10 square 100-10000 synth sin fmod 100 vol -40dB

Check HDA params.
=================
::

  $ sudo apt-get install alsa-tools-gui
  $ hdajackretask

See also:

  http://www.alsa-project.org/main/index.php/HDA_Analyzer
    provides a graphical interface to access the raw HD-audio control

Suitable convertors?
====================
::

  $ sudo apt-get install ffmpeg

or::

  $ sudo apt-get install sox

List of sox supported format: See sox(1).

List of ffmpeg supported format::

  $ ffmpeg -formats

How convert amr to ogg/mp3?
===========================

TODO

How easy convert between mp3/wav/ogg?
=====================================
::

  $ sox in.mp3 out.ogg
  $ sox in.ogg out.wav
  ... etc

How convert flac to mp3?
========================
::

  $ flac -c -d $file.flac | lame -m j -q 0 -V 0 -s 44.1 - $file.mp3

How convert wma to mp3?
=======================
::

  $ mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $file.wma
  $ lame -m s audiodump.wav -o "$file.mp3
  $ rm audiodump.wav

How convert m4a to mp3?
=======================
::

  $ faad -o - $file.m4a | lame -V 0 - $file.mp3

How split mp3/ogg files?
========================

Split mp3 and ogg files::

  $ mp3splt

See::

  http://mp3splt.sourceforge.net/mp3splt_page/home.php
                home page
