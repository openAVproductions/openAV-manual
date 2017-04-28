########
Luppp
########

.. image:: img/luppp/luppp.png
   :align: center

Luppp ist ein Programm zur Musikerstellung – vorallem für den Live-Einsatz. Der
Fokus liegt auf Echtzeitverarbeitung und intuitivem Workflow. Durch
umfangreiche MIDI-Steuerung wird der Einsatz von Loops zum Kinderspiel! In den
nächsten Abschnitten wird beschrieben, wie Luppp zusammen mit JACK für
Audioein- und -ausgabe eingerichtet wird. Außerdem werden die Konzepte von
Szenen und Clips vorgestellt, sodass die Kreativität für Live-Auftritte optimal
genutzt werden kann.

Luppp und JACK
==============

Wenn dir Luppp und Jack komplett neu sind, schaue dir dieses Beispielvideo an,
das eine typische Looping-Session mit Luppp zeigt:
https://www.youtube.com/watch?v=R6WiWDDKRCQ

Bevor wir Loops aufnehmen können, müssen wir eine Audioquelle mit Luppps
“master_in”-Anschluss verbinden. Außerdem müssen “master_right” und
“master_left” mit den Systemanschlüssen (Soundkarte oder Audiointerface)
verbunden werden. Der folgende Screenshot zeigt die Verbindungen:

.. image:: img/luppp/luppp_jack_connections.png
   :align: center

Als nächstes schauen wir uns die Oberfläche von Luppp an. Diese mag auf den
ersten Blick komplex wirken, ist aber wirklich einfach, wenn man die einzelnen
Bereiche ersteinmal versteht.

.. image:: img/luppp/luppp_interface.png
   :align: left

Du siehst acht Tracks mit jeweils zehn Clips. Um zu testen, ob dein Audiosetup
funktioniert, spiele deine Audioquelle ab und du solltest die Amplitude auf der
Anzeige ganz oben rechts sehen. Wenn das klappt, kannst du loslegen!

Nun klicke auf einen Clip, um die Aufnahme zu starten und klicke erneut, um das
Aufgenommene zu loopen. Alle Aktionen in Luppp werden mit dem Takt
synchronisiert. Dieser wird durch die vier Quadrate unten rechts angezeigt.  Du
kannst das Tempo durch Drehen des Reglers mit der BPM-Nummer ändern (der
Standardwert ist 120).

.. image:: img/luppp/luppp_scenes.png
	:align: right

Szenen
======

Ein sehr wichtiges Konzezt von Luppp sind die Szenen. Auf jedem Track kann nur
ein Clip zur gleichen Zeit agbespielt werden. Im Masterbereich von Luppp
befindet sich die Liste der Szenen. Eine Szene kann durch Klicken auf den Namen
gestartet werden, wodurch alle Clips in dieser Reihe gleichzeitig gestartet
werden.

.. Tip::

   Wenn du Clips mit einer Länge von mehr als einem Takt verwendest, achte
   darauf, die Aufnahme zur gleichen Zeit mit dem Start der anderen Clips in
   der Reihe zu starten. Ansonsten kann das Starten einer Szene ein bisschen
   chaotisch werden ;)

-----

.. image:: img/luppp/luppp_track.png
   :align: left

Tracks
======

Alle Tracks in Luppp haben ein paar Regler, um unglaubliche Dinge zu tun. Wir
gehen diese nun von oben nach unten durch. Ganz oben befindet sich der Name des
Tracks. Durch Rechtsklick kannst du diesen ändern. Darunter befindet sich ein
Kreis, der den Fortschritt des momentan abgespielten Loops in diesem Track
anzeigt. Bei der Aufnahme von weiteren Clips in der selben Reihe ist es sehr
hilfreich, den Fortschritt im Auge zu behalten. Als nächstes kommen die Clips.
Auch hier kannst du durch Rechtsklick einen Namen vergeben. Außerdem wird hier
für jeden Clips der momentane Status angezeigt, ob er gerade aufnimmt, abspielt
oder leer ist. Unten befindet sich ein Schieberegler (Fader), mit dem die
Lautstärke des Tracks angepasst werden kann. Um den Fader herum befinden sich
weitere Regler, die wir uns im nächsten Abschnitt ansehen werden.

.. Tip::

    Du kannst die Tastatur verwenden, um die Clips zu steuern. Die Clips der
    ersten Szene haben die Tasten 1 – 8, 9 löst die Szene selbst aus. Die
    darunterliegenden Tastenreihen steuern die folgenden Szenen. Probier’ es
    aus!

-----

Panning
=======

Bevor wir uns der Welt der Bearbeitung in Lupp zuwenden, schauen wir uns eine
einfache, aber wirkungsvolle Funktion an. Es wurde in Version 1.1.1 eingeführt:
das Panning. Der Regler über dem Fader jeden Tracks kann das Signal zum
Masterkanal splitten. Du hast also die Möglichkeit, jedem Kanal einen Platz im
Mix zu geben. Das ist sehr simple, gehen wir also weiter …

FX Section
==========

The first controls under the clip section ist the effect section. In your 
jack connection manager of your choice you will notice the Send_track_X and
Return_track_X ports. Connecting the send to the input of a plugin and the 
output back to the returns of Luppp will send the audio through this plugin. 
To enable the processing, click on the yellow FX Button. With the knob you can
adjust the volume of the effect.
This feature gives you endless possibilities. You could add as many effects as
you want in any order. Just be creative!

Reverb Send
===========

This feature gives you the great possibility to simply add some reverb on a
track. Before we can try, we need to connect Luppps send_out to a reverb of
our choice (eg :ref:`roomy`) and the outputs of the reverb back to Luppps
master_returns. If it's done, we can enable the reverb for each track with
the Snd-Button and adjust the amount of reverb with the above knob. 

The connections for a reverb send are as follows:

.. image:: img/luppp/luppp_reverb_send_connections.png
   :align: center

.. image:: img/luppp/luppp_reverb_roomy.png
   :align: right

And the recommended Roomy settings are shown here - the most important part
is to set the Dry/Wet dial to 100% Wet, as then only the reverb is output,
and the original signal is totally muted. Given that Luppp is already
outputting the original signal, we do not want the reverb to also do that!

There is a video about this topic, too: https://www.youtube.com/watch?v=wLy9oG_WpHg

-----

Sidechaining
============

Using Luppp it's very easy to use sidechaining, for example to create some
house bass lines.. It's a pretty simple concept: you use one audio signal to
control the processing of another signal. This processing could be a
compressor or an enveloper (eg :ref:`ducka`). So, how to use it? At first
we again need to do some connections. Luppps sidechain_key needs to be
connected to a sidechain input and Luppps sidechain_signal needs to be
connected to the regular audio inputs of the Ducka plugin.
Send the outputs of the plugins to the master outputs.

Back to Luppp. On one track you need to enable the Key-Button. This way the
output of the track is the trigger for the sidechain effect. Now you can
send each track with the knob above the Key-Button to the plugin. If you
want to see how it's works, watch these videos: 

* Explanation: https://www.youtube.com/watch?v=-AwtMUeBc9w
* Showcase: https://www.youtube.com/watch?v=bPJQs6w2XQc

Input Section
=============

At the beginning of this tutorial we connected a audio source to Luppps master_in. 
You can input several different sources, or any output of a mixer or what ever you can 
imagine! In the top right corner of the GUI you can see the Luppp Input Section.

.. Tip ::
	Luppp only has a mono input. If you want to connect a stereo source like a synthesizer, 
	there are severel possibilities. In the most cases it's enough to connect just one side since 
	there are equal or similar. If you need both sides, consider a mixer to mix them together.
	But there might be some trouble if you simply connect both to the input port.

Here you have a meter, and a fader to adjust the volume of the input. The knobs below
do the following:

.. image:: img/luppp/luppp_inputsection.png
   :align: left

* Snd-Button activates the Send (Knob above sets the amount, eg Reverb)
* Key-Button sets the input as Key-Signal for Sidechaining 
* Knob above the Key-Button how much of the input goes to the Sidechain-Signal
* Mix-Button activates the routing of the input to the master outs of Luppp
* Knob above the Mix-Button sets amount of the input on the master outs.

So you have great possibilities here: a little reverb on the input, using a 
input for a special sidechaining key? Easy! You can monitor what you play just with 
Luppp and adjust the recorded volume to fit with the other tracks.

Master Section
==============

.. image:: img/luppp/luppp_master_section.png
   :align: right

Lets take a look at the last part of the GUI: the master section. The function of the most elements
are quite obvious, so i will only explain them in short:

* the green, yellow, orange and red square show the beat (from bottom to top)
* the Stop/Play button stops or restarts the transport
* with the tap button you can adjust the tempo by clicking the beat
* the metro button activates a metronom on the headphones_out of Luppp (note that you can choose between a selection of different volume levels by right-clicking on the "metro" button)
* the knob with the number sets the tempo
* the return knob adjusts the volume of the returned audio (eg reverb)
* the fader adjusts the master volume

Konfiguration
=============

Über eine Datei im Konfigurationsordner des Benutzers stellt Luppp
Konfigurationseinstellungen bereit. Hierüber können ein paar Einstellungen
geändert werden, die nicht über die GUI zu erreichen sind.

Diese Konfigurationsdatei findet sich unter
``~/.config/openAV/luppp/luppp.prfs`` und benutzt das `JSON
<https://en.wikipedia.org/wiki/Json>`_-Format.

Die Voreinstellungen sehen wie folgt aus::

    {
        "saveDirectory":                "luppp",
        "resampleQuality":              1,
        "defaultControllers":           [],
        "enablePerTrackSendReturns":    0
    }

Speicherort
--------------

Die Option ``saveDirectory`` definiert den Ordner, in dem Sessions gespeichert
werden. Der Pfad ist relativ zum Benutzerverzeichnis und ist standardmäßig
``luppp``::

    "saveDirectory": "luppp"

Qualität der Abtastratenkonvertierung
-------------------------------------

Die Qualität der Abtastratenkonvertierung kann über die Einstellung
``resampleQuality`` definiert werden. Mögliche Werte sind

* 0 = LINEAR
* 1 = SINC_FASTEST
* 2 = SINC_BEST

Der Standardwert ist ``SINC_FASTEST`` (``1``)::

    "resampleQuality": 1,

Standard-Controller
-------------------

Mit der Option ``defaultControllers`` können Controller definiert werden, die
beim Programmstart automatisch geladen werden. Mehrere Controller können mit
Komma getrennt ngegeben werden::

    "defaultControllers": ["akai_apc.ctlr", "launchpad_s.ctlr"]

Send/Returns pro Track
----------------------

Die Einstellung ``enablePerTrackSendReturns`` kontrolliert, ob
Send/Return-Kanäle für jeden Track bereitgestellt werden sollen.
Ein Wert von ``0`` deaktiviert, ``1`` aktiviert dies::

    "enablePerTrackSendReturns": 0
