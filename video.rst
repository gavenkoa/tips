.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Video.
========
.. contents::

Players for linux?
==================
::

  $ sudo apt-get install vlc
  $ sudo apt-get install mplayer

Determine video format.
=======================
::

  $ file $VIDEO
  $ mplayer -frames 0 -vo null -ao null -identify $VIDEO
  $ mediainfo $VIDEO

See:

  http://en.gentoo-wiki.com/wiki/Show_Video_Codecs
                Show Video Codecs

3d film.
========
::

  $ mplayer -vf stereo3d=side_by_side_left_first:anaglyph_red_cyan_color -vo gl $VIDEO
  $ mplayer -vf stereo3d=above_below_left_first:anaglyph_red_cyan_color -vo gl $VIDEO

See ``man 1 mplayer``.

Web camera.
===========

View picture from web camera on display screen::

  $ mplayer tv://
  $ mplayer tv:// -tv driver=v4l2:width=640:height=480:fps=15:device=/dev/video0
  $ guvcview
  $ cheese
  $ camorama

Make screenshort from web camera::

  $ ffmpeg -f video4linux2 -i /dev/v4l/by-id/CAMERA -vframes 1 test.jpeg
  $ ffmpeg -f video4linux2 -i /dev/v4l/by-id/CAMERA -vframes 4 test%3d.jpeg

Record web camera to a file::

  $ mencoder -fps 15 tv:// -ovc lavc -o my.avi
  $ guvcview

See:

  http://wiki.debian.org/Webcam
                Debian wiki.

Extract audio from video file.
==============================

``$NO`` - autio strean number::

  $ ffmpeg -i $IN -c:a:$NO $OUT.mp3

  $ mplayer -ao pcm:fast:file=audio.wav -vc null -vo null  input.avi

Integrate audio to video file.
==============================
::

  $ mencoder \
    -ffourcc divx \
    -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=400 \
    -audiofile audio.wav \
    -oac mp3lame -lameopts vbr=3 \
    -o output.avi input.mkv

Synchronise video and audio streams.
====================================
::

  $ mencoder -delay 0.7 -oac copy -ovc copy in.avi -o out.avi
  $ mencoder -mc 0 -of lavf -lavfopts format=mp4 -oac lavc -ovc lavc \
    -lavcopts aglobal=1:vglobal=1:acodec=libmp3lame:abitrate=128:vcodec=mpeg4:vbitrate=500:keyint=200
    -vf scale=-3:240,crop=320:240,harddup -af lavcresample=44100 -o out.mp4 in.mp4

Convert video for Nokia 5320.
=============================
::

  $ mencoder -mc 0 -of lavf -lavfopts format=mp4 \
    -oac lavc -ovc lavc \
    -lavcopts aglobal=1:vglobal=1:acodec=libmp3lame:abitrate=96:vcodec=mpeg4:vbitrate=400:keyint=100 \
    -vf scale=-3:240,crop=320:240,harddup -af lavcresample=44100 -ofps 15 \
    -o out.mp4 in.avi

How convert .3gp to .avi(mpeg)?
===============================
::

  $ sudo apt-get install ffmpeg
  $ ffmpeg -i test.3gp -f mpegvideo -ar 44100 -ac 1 -acodec mp3 test.mpg
  $ for i in `ls -1 *.3gp | cut -d. -f1`; do ffmpeg -y -i $i.3gp -sameq -f mpegvideo -s cif -r 25 -ar 32000 -ac 1 mpegs/$i.mpg; done
  $ ffmpeg -i video-in.3gp -b 250 -s 160×120 -r 15 -f avi -an video-out.avi
  $ mencoder -oac mp3lame -ovc lavc -o video-out.avi -vf pp,2xsai,scale video-in.3gp
  $ mencoder -o video-in.avi -vf pp,2xsai,scale -ovc lavc video-out.3gp
  $ mencoder -o video-in.avi -vf rotate=2 -oac pcm -ovc divx4 video-out.3gp

You need to compile FFmpeg with AMR support (--enable-amr_nb --enable-amr_wb).

AMR WB FLOAT NOTICE ! Make sure you have downloaded TS26.204
V5.1.0 from
http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-510.zip
and extracted the source to libavcodec/amrwb_float


AMR NB FLOAT NOTICE ! Make sure you have downloaded TS26.104
REL-5 V5.1.0 from
http://www.3gpp.org/ftp/Specs/latest/Rel-5/26_series/26104-5??.zip
and extracted the source to libavcodec/amr_float
and if u try this on an alpha, u may need to change Word32 to int in
amr/typedef.h

Video editors.
==============
::

  $ sudo apt-get install pitivi kino

See:

  http://www.pitivi.org/
                pitivi home page.
  http://www.kinodv.org/
                Kino home page.

