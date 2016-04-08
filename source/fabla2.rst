
.. _fabla2:

#######
Fabla2
#######

Fabla2 is a drum sampler :ref:`lv2_plugin` instrument. It is ideal for
loading up your favorite sampled sounds and bashing away on a MIDI
controller. Or if it’s crafty beat programming your after that’s cool too!

The next section introduce the features that Fabla2 has, how to record your
own drum sounds, create professional-sounding multi-layered kits,
and use advanced features like OpenAV's :ref:`auxbus`.

.. _fabla2_features:

Features
==========

Fabla 2.0 has all of the "normal" features you've come to expect of a
professional software sampler. Some examples are multi-layer support,
banks, ADSRs, start and end points, volume controls... but Fabla2 provides
more than this! With AuxBus sends, per-voice FX and an intuitive interface,
Fabla2 becomes a live-performance sampler with huge improvements in
features and workflow compared to a simple sampler like Fabla 1.0.

Internal Effects
----------------
.. warning::
	The internal FX is a work-in-progress feature of Fabla2, and may
	be disabled in your current version. When testing is complete, it
	will be enabled by default.

Fabla2 has internal effects that run *per voice*. This means that if one
audio sample is played twice, any FX will be running twice, independantly.
Although the sample data is constant, the sound is different because
the FX parameters may have changed, keeping the listener interested.

SVF Filter
~~~~~~~~~~
Each voice has a :abbr:`SVF (State Variable Filter)` filter capable of
highpass, lowpass and bandpass.  This filter can be set to a specific
frequency, or can be dynamically adjusted by the velocity of the MIDI
note-on event.

Distortion
~~~~~~~~~~
Theres very little as good a spicing up a few samples as some old-school
crunchyness - and this distortion is well capable of destroying audio.

AuxBus
------
The :ref:`auxbus` feature is an advanced and complex tool - but it also provides
very flexible routing and awesome musical configurability. If you are
familiar with routing of audio-signals, and want to understand more of what
the auxbus feature can offer you, read the AuxBus Integration section.

____

.. _fabla2_creating_kits:

Creating Kits
=============
This section introduces how to create your own drumkits with Fabla2. First
the basics are introduced - loading single samples, and levelling the
volume. The following sections show how to set up multi-layer samples,
use the FX sends, and show examples.


Building a Basic Kit
--------------------
For this tutorial, we rebuild a basic drum kit using "one-shot" samples.
The samples we will use have been recorded by OpenAV, and can be
downloaded from `this link on the OpenAV website
<http://openavproductions.com/downloads/savageDrums.zip>`_. The .zip
contains a simple kick drum, hi-hats, snare and a ride cymbal.

.. image:: img/fabla2/fabla2_load_sample.png
   :align: left

Loading Samples
~~~~~~~~~~~~~~~
Launch Fabla2 as described in the beginners guide :ref:`launching_a_plugin`
section. When the interface opens, click the pad you want to load a sample
to. Now we're going to click the "File" button, browse to the location
where your have samples, and select a sample filename to audition it.

.. Tip::
	Right click on a pad, the File browser will open.

Click on a different pad, and load another sample. Keep the layout of the
samples logical, particularly if you use a MIDI keyboard or drum-pad to
trigger notes. When all samples are loaded, continue reading!

Volume Levels
~~~~~~~~~~~~~
.. note::
  The audio can be amplified as well as attenuated - if all controls are
  turned up, the audio will become very loud and distroted!
Setting volume levels in Fabla2 is easy - but there are 3 points where volumes
can change, and 3 places where the audio can be sent to an output. It is
good practice to keep the volume at a reasonable level at all points in the
signal path, as this makes using pre and post fader sends much easier. The
following list shows the signal-chain for volumes:

* Audio Sample Volume
* Pre-Fader output
* Pad Volume
* Post-Fader output
* Master Volume
* Master Output

Audio sample volume can be changed in the Pads view, see the "Gain" dial.
The pre-fader output is set by both the send amount, and the sample volume.
The Pad volume can be changed using the fader in the Pads view, or Live
view. The Audio sample volume affects the Pad volume too - but the
pre-fader does not.
Post-fader output is set by the audio-sample volume, pad volume and send
amount.
The master output volume is set by audio-sample amount, pad volume and
master volume dials.

.. todo::
	How to use the Live view to adjust the volume levels.
	Images of Fabla2 showing volume for use cases:
	(1) Sample is very quite, no sends, just master output
	(2) Sample is too loud, reverb send, lots of headroom on output

Multi-layered Kits
------------------
When multiple samples are loaded to one pad, Fabla2 has multiple ways of
using the samples.

.. todo::
	Check SAMPLE_SWITCH_SYSTEM in code, ensure order is correct. This
	needs to be done post-pull request that hasn't been merged yet.

1. None: Play the last-used sample (Aka, ignore the others)
2. Round-Robin: move to the next sample when one is played
3. Velocity Layers: Choose a sample based on the note-on velocity and its
   velocity map.
4. Volume: Same as None, but change the volume of the sample based on
   velocity.

What sample switching mode will sound the best depends on the samples in
use. If the samples are increasing in intensity use "velocity layers". If
the samples are all the same intensity but vary in the recording, "Round
Robin" is a good choice. If you have one sample, and wish to add "dynamics"
when sequencing it, choose "volume". If the goal is to achieve the exact
same every time, leave the sample choice dial on "None".

.. _fabla2_manipulating_samples:

Manipulating Samples
====================

.. todo::
	Fill out this section, with examples of how each feature is useful
	in a particular musical context.

How can F2 manipulate audio that's recorded?
* Filters
* Other FX
* AuxBus FX sends
* Velocity -> Volume mapping?
* Other mappings?
