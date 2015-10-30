.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

========
 Image.
========
.. contents::

Viewers.
========

GraphicsMagick.
---------------

GraphicsMagick command-line utilities to create, edit, or convert images.

ImageMagick.
------------

ImageMagick - is a free software suite for the creation, modification and
display of bitmap images.

gthumb.
-------

gThumb is an advanced image viewer and browser. It has many useful features,
such as filesystem browsing, slide show, image catalogs, web album creation,
camera import, image CD burning, batch file operations and quick image editing
features like transformation and color manipulation.

qiv.
----

Quick image viewer for X.

Free art.
=========

  http://openclipart.org/
                home page

Join icons to sprite.
=====================

Make one liner::

  $ convert *.png -append sprites.png  # vertically
  $ convert *.png +append sprites.png  # horizontally

Make box (with auto size)::

  $ montage -background transparent --geometry 16x16  *.png sprites.png

Make box with signs::

  $ montage -font Bitstream-Vera-Sans-Mono -pointsize 8 -set label '%f\n%wx%h' \
            -background white --geometry 16x16  *.png sprites.png

To get list of available font names::

  $ identify -list font

Make box with selected width or height::

  $ montage -tile 2x *.png sprites.png
  $ montage -tile x3 *.png sprites.png
  $ montage -tile 3x4 *.png sprites.png

Remove EXIF data.
=================
::

  $ sudo apt-get install libimage-exiftool-perl
  $ exiftool -all= *.jpg

  $ sudo apt-get install exiv2
  $ exiv2 rm *.jpg

  $ sudo apt-get install imagemagic
  $ convert -strip FROM.jpg TO.jpg
  $ mogrify -strip PIC.jpg

