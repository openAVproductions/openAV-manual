
.. _artyfx:

########
ArtyFX
########

ArtyFX ist eine Sammlung von Audio Effekten, die sowohl einzeln verwendet
werden können, als auch in vielen komplexeren OpenAV-Projekte wie Fabla2, 
Sorcer und Luppp eingebaut sind. Jeder Effekt kann individuell als LV2-plugin
verwendet werden.

Zu ArtyFX gehören viele verschiedene Plugins - alle "klassischen" Effekte wie 
Hall, Echo und Filter sind enthalten. Die folgenden Abschnitte beschreiben 
jedes Plugin im Detail und beschrieben die Verwendung.

Hast du neue Vorschläge für ArtyFX? Kontaktiere OpenAV!


____

.. image:: img/artyfx/artyfx_bitta.*
  :align: right
.. _bitta:

Bitta
=======

Bitta ist ein Bitcrusher-Plugin. Der Effekt reduziert die
:abbr:`Bittiefe(Die Auflösung der Lautstärke eines Audio-Signals)` des 
Signals. Da die Verzerrung von der Lautstärke des Eingangssignales 
abhängig ist, sollte der "Crush"-Regler vorsichtig verwendet werden.

* Crush : Ändert die Zahl der Bits für den Effekt.

____

.. image:: img/artyfx/artyfx_della.*
  :align: left

.. _della:

Della
=======

Della ist ein BPM-abhängiges Echo, mit einstellbarem Feedback und Echo 
Lautstärke.

* "Feedback" reguliert die Lautstärke des Signals, das zurück zum Echo 
  geführt wird. Dreh es auf um dieses verrückte Reaggae-Dub-Echo zu erzeugen,
  das für immer anhält!

* "Volume" ändert die Lautstärke des verzögerten Signals: Das ist nützlich,
  um das Echo im Hintergrund der Spur zu halten.

* "Time" ändert die Länge des Echos in Abhängigkeit zu den BPMs. Es springt
  also zwischen der Länge von 1/8, 1/4, 1/2 und einer ganzen Note. Della nimmt
  die BPM vom Plugin-Host. Dadurch bleibt das Echo synchronisiert, wenn man das 
  Tempo ändert.

____

.. image:: img/artyfx/artyfx_ducka.*
  :align: right

.. _ducka:

Ducka
=======
Ducka is a side- chain envelope plugin: it is very useful for creating
"pumping" basslines as often found in minimal house music. The plugin works
by analysing the volume of a sidechain input, and changing the volume of a
separate stereo track, based on the amplitude of the sidechain input.

* Threshold sets the level that the input audio must reach before the
  stereo track gets reduced.

* The drop controls the amount of volume reduction that is performed.

* Time controls the amount of time it take before the stereo track is faded
  in again. Note that this control is BPM dependant, and the center is
  directly on the off- beats. A setting of half (its default) is generally
  musical :)

____

.. image:: img/artyfx/artyfx_driva.*
  :align: left

.. _driva:

Driva
=======

Driva is a multi-distortion unit capable of the most mean and gritty distortions.

* Tone : Click the Tone button, a list of different distortion models are
  available. Just click the desired distortion, and keep rocking out.
  Cancel at the bottom quits the tone-change view.

* Amount just cranks up the gain / distortion quanitity. Use at your own
  peril!


____

.. image:: img/artyfx/artyfx_filta.*
  :align: right

.. _filta:

Filta
=======
Filta is a lowpass and highpass filter combination. Useful to remove
unwanted high and low frequencies from various recordings or instruments.A

* Frequency controls what type of filtering is done, and what frequency.
  Lower values are lowpass filter, turning up the dial is causes highpass.


____

.. image:: img/artyfx/artyfx_kuiza.*
  :align: left

.. _kuiza:

Kuiza
=======
Kuiza is a 4 band equalizer. Its perfect for creatively shaping the sound
of an instrument or synth. Each of the gain controls changes the amplitude
at the given frequency. The master gain can be used to reduce or amplify
the overall volume if needed. The controls (left to right):

* Low      (   ~55 Hz)
* Low mid  (  ~220 Hz)
* High mid ( ~1760 Hz)
* High     ( ~7040 Hz)
* Master Gain

____

.. image:: img/artyfx/artyfx_masha.*
  :align: right

.. _masha:

Masha
=======
Masha is a beat grinder plugin: it records a segment of audio and plays it
back as a loop, causing a "stutter" effect.

* Volume changes the loudness of the stutter-loop. PassThru allows bleeding
  the normal signal trough. Time is a BPM dependant control that changes
  the loop-record and playback length. Gradually reduce this value to get
  that "standard" DJ stutter effect!
* This effect has some special functionality, to allow manual control over
  the BPM. Usually the BPM will be taken from the host program (or JACK
  transport), but it can now be controlled by a dial.
* The "HostBPM" button controls the BPM source. When the button is blue,
  the HostBPM is enabled. Turning the button off makes the manual BPM dial
  appear. The dial also shows the current BPM.

____

.. image:: img/artyfx/artyfx_panda.*
  :align: left

.. _panda:

Panda
=======
Panda is a compressor expander combo, with attack and release controls.

* Threshold: the "turning point" of compression / expansion. Turning down
  the dial expands the signal, turning it up causes compression.
* Release changes the time for Panda to fade-out its compression/expansion.
* Factor controls the amount of compression/expansion performed, the
  "maximizer" dial.

____

.. image:: img/artyfx/artyfx_roomy.*
  :align: right

.. _roomy:

Roomy
=======
Roomy is a spacious and smooth reverb.

* The Time control changes the length of the reverb tail: higher values
  give will create a bigger and more spacious mix.
* Damping controls the high- frequency damping: lower settings gives a
  spacious open sound, while a high damping feels small and close.
* The Dry/Wet control changes the amount of reverb signal mixed in: useful
  for techno and trance "reverb builds"... just crank it right up!


____

.. image:: img/artyfx/artyfx_satma.*
  :align: left

.. _satma:

Satma
=======
Satma is a crazy distortion plugin. Useful to excite and get gritty, dirty
audio.

* Distortion changes the amount of signal-shaping that occurs: the overall
  amount of noise production.
* The Tone control subtly varies between high-frequencies and lower
  frequencies, or making both equally gritty.



____

.. image:: img/artyfx/artyfx_vihda.*
  :align: right

.. _vihda:

Vihda
=======
Vihda is a stereo-enhancer, using a mid-side matrix.

* The Width parameter affects the amount of stereo content in the signal.
  Note that the the mid-side technique only enhances stereo: it does not
  create it!
* The Invert button inverts the right channel, which can cause a perceptual
  wider mix due to how the brain interprets audio. Try it and see if it
  sounds good.
