
.. _beginner_setup:

###############
Beginner Setup
###############

Welcome to the exciting world of Linux Audio! Although Linux audio is in
general a bit more technically demanding of the musician using it, there
are great rewards in understanding the technology you're using, and being
able to adapt that tech to do exactly what you want. OpenAV software
targets *you* - the live performing musician - and if you have feedback on
our software please do `get in touch`_!

.. _get in touch: http://openavproductions.com/contact/

This page will introduces the beginner on how to use OpenAV software,
how to set up JACK, launch LV2 plugins with Jalv, and answers other common
questions.

.. _lv2_plugin:

LV2 Plugin
==========

LV2 Plugins are extensions to any audio application. Each plugin contains
functionality or features, which is made available when a host-program
loads the plugin. LV2 is an open-source plugin API, which means it can be
freely used by everybody - no contracts or proprietary copyrights here!

OpenAV builds LV2 plugins, as the LV2 plugin spec is very powerful,
flexible and extensible. This allows complex plugins like samples and
synths to be created by OpenAV, and easily used in DAWs like Ardour,
Audacity and many others!

To list all installed plugins on your system, run the following command
from a terminal ``lv2ls``.  The output is a long list of URI items, which
identify each plugin that is available on your system. These URIs will be
used later in the :ref:`launching_a_plugin` section. An example of one URI
is ``http://www.openavproductions.com/artyfx#roomy``.

To see more (technical) information about an LV2 plugin, we can get the
information about each plugin using ``lv2info`` and passing that command a
URI. Example output for :ref:`Roomy` is as follows:

.. literalinclude:: cmdoutput/lv2ls_roomy.txt

.. _jack:

JACK
====

JACK is a program that lets you run audio applications, and route audio
between them. Here at OpenAV we *always* have JACK running when developing
software - its the back-bone of linux-audio - so get used to it!

.. _starting_jack:

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
program, which natively speaks to JACK. The :ref:`launching_a_plugin`
section shows you how to launch plugins using JALV.

.. _launching_a_plugin:

Launching an LV2 Plugin
=======================

This section shows you how to launch a plugin using JACK as the audio
backend, and Jalv to host LV2 plugins. LV2 plugins are identified by URIs,
refer to the :ref:`lv2_plugin` section how to list available plugins.

* Start JACK. If you have not started jack before, see the :ref:`starting_jack` section.
* Launch Roomy in Jalv using the following command: ``jalv.gtk http://www.openavproductions.com/artyfx#roomy``
* Use :ref:`qjackctl` to connect the ``System:capture`` to ``Roomy:in`` and ``Roomy:out`` to ``System:playback``

That's it! Any sound that gets captured by the soundcard hardware will have
:ref:`Roomy` effect the signal, and it will be played back over the
speakers!
