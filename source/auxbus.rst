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

Describe signal routing here, briefly mention some different use cases, and
that there are post and pre fader AuxBusses

Side-Chaining
-------------
A side-chain is one use-case for an AuxBus. Side-chaining involves copying
a signal from one place, and using it to effect another audio stream
somewhere else. The naming of the signals can be confusing, so for clarity
this article defines the following:

  key    : The audio taken from a source, used to influence another signal.
           Often a mono signal, as only the amlitude is generally used.
           Note that the key signal is *NOT* audible!

  content : The audio that will be influenced by the side-chain.
	This is usually a stereo signal, and the side-chain-FX output will
	be audible to the audience.

Sidechaing works by taking the amplitude of the key signal, and performing
an action on the content signal based on it.

For example, Ducka from ArtyFX changes the volume of the content signal,
based on the amplitude of the key signal. This is called side-chain
eveloping.

.. note::

	Quite often you'll hear the term "sidechain" and
	"sidechain-compression" mixed up. Although not strictly the same as
	using an envelope to change the volume, the audible effect is
	almost identical. This is left over from when an analog
	compressor would be "abused" to change the volume of a signal by
	compressing it so hard that it would not be audible!

Send FX
-------
Another common use-case for AuxBus is reverb sends.
