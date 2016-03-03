########
Sorcer
########

Sorcer is a polyphonic wavetable synth LV2 plugin. Its sonic fingerprint is
one of harsh modulated sub-bass driven walls of sound. Two morphing
wavetable oscillators and one sine oscillator provide the generation
routines. The LFO can be mapped to wavetable modulation as well as filter
cutoff. An ADSR allows for shaping the resulting sound, while a master
volume finishes the signal chain. Easily creating a variety of dubstep
basslines and harsh pad sounds.

Wavetables
==========
Wavetables are short recordings of a single-cycle off sound. This allows
the synth to repeatedly play the same cycle of audio, and create a
continuous tone which has a specific timbre due to the harmonics in the
recorded audio.


Limitations
-----------
Describe some limitations of single-cycle wavetables here.

Aliasing and Artifacts
----------------------
Note that wavetable synthesis generally has some side effects. Playing a
sample back at a different rate (altering the speed) creates some
artifacts. With playback rates close to :abbr:`unity(The playback rate of 1,
also the original playback rate)` these artifacts can be audible unless
some :abbr:`interpolation(smoothing of audio data based on the
playback rate)` is done.

