##########
Fabla 2.0
##########

Fabla is an open-source LV2 drum sampler plugin instrument. It is ideal for
loading up your favorite sampled sounds and bashing away on a MIDI
controller. Or if it’s crafty beat programming your after that’s cool too!
The ADSR envelope allows the shaping of hi-hats and kicks while the
compressor beefs up the sound for those thumping kicks!  

Features
==========

Fabla 2.0 has all of the "normal" features you've come to expect of a
professional software sampler. Some examples are multiple layers, a few
banks, an ADSR and volume control per sample.

Internal Effects
================
Fabla2 has internal effects that run *per voice*. This means that if one
audio sample is played twice, the filter will be running twice,
independantly. This means that although both the samples are the same,
they will sound different, keeping the listener interested.

SVF Filter
----------
Each voice has a :abbr:`SVF (State Variable Filter)` filter capable of
highpass, lowpass and bandpass.  This filter can be set to a specific
frequency, or can be dynamically adjusted by the velocity of the MIDI
note-on event.

Distortion
----------
Theres very little as good a spicing up a few samples as some old-school
crunchyness - and this distortion is well capable of destroying audio.


AuxBus
=======
The AuxBus feature is an advanced and complex tool - but it also provides
very flexible routing and awesome musical configurability. If you are
familiar with routing of audio-signals, and want to understand more of what
the auxbus feature can offer you, read the AuxBus Integration section.

