.. image:: img/fabla/fabla.png
   :align: right
   :scale: 50 %

########
Fabla
########

Fabla is an open-source LV2 drum sampler plugin instrument. It is ideal for loading up your favorite sampled sounds and bashing away on a MIDI controller. Or if it’s crafty beat programming your after that’s cool too! The ADSR envelope allows the shaping of hi-hats and kicks while the compressor beefs up the sound for thumping kicks!

.. note:: The source code is available from the `Fabla page on Github`_
	but your package manager probably has a pre-compiled version!

.. _Fabla page on Github: https://github.com/openAVproductions/openAV-Fabla/

____

Sampling
========

Fabla is a simple sampler, which loads an audio file (.wav or similar) and
can play it back when MIDI notes are sent to it. Fabla does not have fancy
features like layers, per-pad FX, or advanced routing. OpenAV is working
on Fabla2, which will include those features, however it is not ready for
use by musicians yet.

For creating electronic drums or heavily sampled music genres like
hip-hop, reggae and dnb, Fabla's features are enough to create music. If
you want to simulate acoustic drums, DrumGizmo is the plugin to use, or
Hydrogen for a stand-alone app.

Pads
----

Fabla uses the concept of pads to load audio samples. There are 16 pads in
the main view of Fabla, each of which can load a single .wav sample. To
load a sample, right click on the pad, and browse to the sample you want
to have loaded. Fabla will load the file from disk, and clicking the pad
will now result in the sample being played back. The waveform display at
the top will show the waveform of the sample that was just played.

.. image:: img/fabla/adsr_select.gif
   :align: right
   :scale: 60 %

ADSR
----

The ADSR available in the top right of the GUI allows shaping of each pads
envelope. When a pad is clicked on, the ADSR shows the currently highlighted
pad in orange (see GIF animation to right). As new pads are clicked, the
ADSR updates to control that sample.

Presets
=======

Fabla supports presets through the LV2 State extension, which most LV2
hosts support. If you have a preset (with shareable, royalty-free samples)
and you'd like to contribute it to OpenAV, please `get in contact`_!

Currently Fabla comes bundled with four presets:
 * fablaHardElectro
 * fablaSavageDrums
 * fablaEasternHop
 * fabla808

Conclusion
==========

Fabla is a capable sample-playback tool, and allows making of electronic
beats as well as sampling existing content and arranging it into new songs.
If you like Fabla, and you're techie and interested in Fabla2, it is
possible to compile the Fabla2 source and test it yourself! Any questions,
do `get in contact`_ OpenAV and we'll try help you as much as we can!

.. _get in contact: http://openavproductions.com/about/

