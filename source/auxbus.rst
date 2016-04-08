.. _auxbus:

########
AuxBus
########

AuxBus is an advanced routing feature, which OpenAV has designed and
implemented. Its focus is on live-performance, and routing audio signals
between different software components in a musical and powerful way. This
article will introduce why AuxBus is such a powerful tool, and how you can
incoperate it in your musical workflow.

Signal Routing
==============

Routing audio is the action of transferring audio between two places.
Traditionally this was done between two seperate pieces of hardware, and a
patch cable was used. Today software contains the same concepts, that audio
can be sent from one location and received at another.  Common use cases
for routing audio are to apply reverb to multiple instruments at once, or
to add FX that would otherwise not be available.

AuxBus is a particular way of thinking about signal-routing. It provides
powerful routing capabilities in a simple and musical way.


Example Uses
============

This  section shows several use-cases of the AuxBus feature.

Reverb Send
-----------

A reverb send is a very common way of applying reverb to a mix. Multiple
instruments are sent to a bus, and the bus has a reverb effect. The reverb
is usually set to be 100% wet signal, as this allows an instruement to
remain at a constant volume in the mix while more reverb can be added.
The :ref:`roomy` reverb from :ref:`artyfx` has the capability to output 100% wet.

.. note::
	TODO miniLAC: Fabla2 routing of AuxBus image

The power of the AuxBus feature in Fabla2 is that internally, each sample
can be routed to every AuxBus a different amount. This means that a snare 
drum can be sent to a reverb send, while a kick drum in the same kit is
not. This is a necessary feature to provide good workflow when doing FX
processing with drum kits, or any sample based instruments.


Side-Chaining
-------------

Side-chaining is an advanced use-case where the power of the AuxBus feature
really shows. To sidechain audio, we copy a signal from one place, and use
it to effect another audio stream somewhere else. The naming of the signals
can be confusing, so for clarity this article defines the following:

key
	The audio taken from a source, used to influence another signal.
	Often a mono signal, as only the amlitude is generally used.  Note
	that the key signal is *NOT* audible!

content
	The audio that will be influenced by the side-chain.
	This is usually a stereo signal, and the output will be audible at
	the output.

Sidechaing works by taking the amplitude of the key signal, and performing
an action on the content signal based on it.

For example, :ref:`ducka` from :ref:`artyfx` changes the volume of the
content signal, based on the amplitude of the key signal. This is called
side-chain eveloping.

.. note::

	Quite often you'll hear the term "sidechain" and
	"sidechain-compression" mixed up. Although not strictly the same as
	using an envelope to change the volume, the audible effect is
	almost identical. This is left over from when an analog
	compressor would be "abused" to change the volume of a signal by
	compressing it so hard that it would not be audible!
