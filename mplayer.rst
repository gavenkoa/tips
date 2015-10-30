.. -*- coding: utf-8; -*-
.. include:: HEADER.rst

==========
 mplayer.
==========
.. contents::

Increase volume above sound cards maximum volume.
=================================================
::

  $ mplayer -af volume=<v>:<sc> media.avi

``<v>`` is the desired gain in dB for all channels in the stream from -200dB to
+60dB, where -200dB mutes the sound completely and +60dB equals a gain of 1000
(default: 0).

``<sc>`` Turns soft clipping on (1) or off (0). Soft-clipping can make the sound
more smooth if very high volume levels are used. Enable this option if the
dynamic range of the loudspeakers is very low.

Maximizes the volume without distorting the sound::

  $ mplayer −af volnorm media.avi
