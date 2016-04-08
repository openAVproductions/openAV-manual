
.. _beginner_setup:

###############
Beginner Setup
###############

This page will introduces the beginner on how to use particular parts of
OpenAV software, setting up JACK, launching LV2 plugins using Jalv, and
lots of other common beginner issues.

.. _lv2_plugin:

LV2 Plugin
==========
Introduce LV2 here, and that OpenAV builds LV2 plugins, which can then be
easily used in a live context with JACK and JALV.

.. _jack:

JACK
====

JACK is a program that lets you run audio applications, and route audio
between them. Here at OpenAV we *always* have JACK running when developing
software - its the back-bone of linux-audio - so get used to it!

Starting JACK
-------------

Command Line
~~~~~~~~~~~~
To have full control over your audio setup, start JACK from the
command-line. This may seem overkill, but OpenAV assures you, it will save
you some headaches. Skip to :ref:`QJackCtl` if you want to use a GUI
program.

The following command will (probably) work pretty well: try it.

``jackd -P 85 -dalsa -dhw:0 -r48000 -p128 -n 2 -Xseq``

The following should be the output of that command::

  JACK compiled with System V SHM support.
  loading driver ..
  apparent rate = 48000
  creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|32bit
  configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
  ALSA: final selected sample format for capture: 32bit integer little-endian
  ALSA: use 2 periods for capture
  ALSA: final selected sample format for playback: 32bit integer little-endian
  ALSA: use 2 periods for playback
  creating alsa_midi driver ...

OK - JACK is now running, and if it doesn't print anything more - the we're
all set! Sometimes though, JACK prints these::

  **** alsa_pcm: xrun of at least 213428.124 msecs

This means the computer can't keep up - usually a sign that the computer
needs to be `configured for real-time audio <http://openavproductions.com/real-time-latency-tuning/>`_, or if the computer really is
15+ years old, perhaps its just not fast enough.

.. _qjackctl:

QJackCtl
~~~~~~~~
If you want to use a GUI program to configure and start JACK, QJackCtl will
do exactly that for you. A very verbose and good tutorial is available from
`LibreMusicProductions site
<http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack>`_.

.. _jalv:

JALV
====
JALV is a small tool that will load an LV2 plugin, and run it in JACK.
This is very useful to run an OpenAV plugin as if it was a standalone
program, which natively speaks to JACK.

.. _launching_a_plugin:

Launching an LV2 Plugin
=======================
.. todo::
	This section describes how to launch a plugin of choice, and then
	connect it to the speakers. Very simple, lots of screenshots.
