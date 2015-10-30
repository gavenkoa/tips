.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

============
 Screncast.
============
.. contents::

VLC.
====
::

  $ cvlc screen:// --screen-mouse-image cursor.png --screen-fps=12 \
    --screen-width=1680 --screen-height=1050 --no-sout-audio --sout \
    "#transcode{venc=theora,quality:10,scale=0.75,fps=12}:duplicate{dst=std{access=file,mux=ogg,dst=desktop.ogg}}}"

  $ cvlc screen:// --screen-fps=12 --screen-mouse-image=e:/home/.icon/cursor.png --no-sout-audio --sout \
    "#transcode{venc=x264,quality:100,scale=1,fps=12}:duplicate{dst=std{access=file,mux=mp4,dst=desktop.ogg}}}"

Available options:

  screen-caching <integer>
                Time in milliseconds.
  screen-fps <integer>
                Capture frames per second (0 default).
  screen-top <integer>
                The top edge coordinate of the subscreen.
  screen-left <integer>
                The left edge coordinate of the subscreen.
  screen-width <integer>
                The width of the subscreen.
  screen-height <integer>
                The height of the subscreen.
  screen-mouse-image <filename>
                Mouse pointer image to use.

vnc2flv.
========

In order to rrecord require VNC server running on host.

  http://www.unixuser.org/~euske/python/vnc2flv/index.html
                home page

libav.
======
::

  $ sudo apt-get install libav-tools

  $ avconv -f x11grab -s cif -r 25 -i :0.0 /tmp/out.mpg
  $ avconv -f x11grab -s cif -r 25 -i :0.0+10,20 /tmp/out.mpg


ffmpeg.
=======

Only video::

  $ ffmpeg -f x11grab -r 25 -s cif -i :0.0 out.mpg
  $ ffmpeg -f x11grab -r 25 -s 1024x768 -i :0.0 out.mpg

Video with audio::

  $ ffmpeg -f oss -i /dev/audio -f x11grab -s cif -r 3 -ab 11 -i :0.0 out.mp4

Oprsions description:

 * ``-r`` frames per second
 * ``-s`` resolution

recordMyDesktop.
================
::

  $ recordmydesktop --no-sound --windowid $(xwininfo | awk '/Window id:/ {print $4}')

Screenshort movies.
===================

Screenshort movie by mencoder.
------------------------------
::

  $ mencoder "mf://*.jpg" -mf fps=30 -o output.avi

Screenshort movie by ffmpeg.
----------------------------
::

  mplayer -ao null -ss 0:0:33 -endpos 2 eagles.avi -vo jpeg:outdir=~/dir
  mplayer -ao null -ss 0:0:33 -endpos 2 eagles.avi -vo png:z=9:outdir=~/dir

Here:

 * ``-ss`` tells mplayer where you begin
 * ``-endpos`` tells mplayer where to stop (minutes)
 * ``z=9`` sets compression level

ImageMagic and shell script.
----------------------------
::

  #!/bin/bash
  let iter=1
  while [ "$iter" -le "$stop" ]; do
    import $iter.png
    sleep 1
    let x+=1
  done

If you interesting in capturing specific window - by 'xwininfo' find,
intereesting your window id (hex value) and use command::

  import -window $windowid $iter.png

To quick view result run::

  $ cd $img_dir
  $ animate -delay 20 *.png
  ^C

To compound image together::

  $ convert -delay 20 *.png capture.mng  # license free, multi-image file format
  $ convert -delay 20 *.png capture.gif

You can add text to pictures before compound theirs::

  $ mogrify -fill yellow -draw 'Rectangle 10,10 150,30' -fill black -pointsize 14 \
     -draw 'text 15,25 "by http://example.com"' $iter.png

If screen capturing slow for you use MIFF file format.

Use root flag to capture all screen::

  $ import -window root $iter.png

  http://linuxdevcenter.com/pub/a/linux/2004/03/04/screen_capture_movies.html
                Making Screen-Capture Movies by Robert Bernier

