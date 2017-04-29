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

FX-Bereich
==========

Die Regler direkt unter dem Clip-Bereich sind der Effektbereich. In dem
JACK-Verbindungsmanager deiner Wahl werden dir die „Send_track_X“- und
„Return_track_X“-Anschlüsse aufgefallen sein. Die Verbindung des
„send“-Anschlusses mit dem Eingang eines Plugins und des Ausganges mit dem
„return“-Anschluss von Luppp leitet das Audiosignal durch dieses Plugin. Um die
Bearbeitung zu aktivieren, klicke auf die gelbe FX-Schaltfläche. Mit dem
Drehregler kannst du die Lautstärke des Effekts regeln. Diese Funktion gibt dir
endlose möglichkeiten. Du kannst beliebig viele Effekte hinzufügen, in der
Reihenfolge deiner Wahl. Sei einfach kreativ!

Halleinbindung
==============

Diese Funktion gibt dir die großartige Möglichkeit, leicht etwas Hall zu einen
Track hinzuzufügen. Bevor wir dies ausprobieren können, müssen wir Luppps
„send_out“-Anschluss mit einem Halleffekt verbinden (z. B. :ref:`roomy`) und
die Ausgänge des Halls an die „master_return”-Anschlüsse von Luppp. Ist das
erledigt, können wir den Hall für jeden Track mittels der „Snd”-Schaltfläche
aktivieren. Mit dem Drehregler darüber kann die Stärke des Halls bestimmt
werden.

Die Verbindungen für einen Halleffekt sehen wie folgt aus:

.. image:: img/luppp/luppp_reverb_send_connections.png
   :align: center

.. image:: img/luppp/luppp_reverb_roomy.png
   :align: right

Die empfohlenen :ref:`roomy`-Einstellungen sind in diesem Screenshot
abgebildet: Am wichtigsten ist es, den „Dry/Wet“-Regler auf „100% Wet“ zu
stellen, da dadurch nur der Hall ohne das originale Signal ausgegeben wird. Da
das originale Audiosignal bereits von Luppp ausgegeben wird, wollen wir nicht,
dass der Reverb dies noch zusätzlich tut!

Zu diesem Thema gibt es auch ein video: https://www.youtube.com/watch?v=wLy9oG_WpHg

-----

Sidechaining
============

Luppp macht die Verwendung von Sidechaining sehr einfach; zum Beispiel das
Erstellen einer House-Bassline … Das Konzezpt ist einfach: Du verwendest ein
Audiosignal, um die Manipulation eines anderen Signals zu steuern. Als
Manipulation könnte ein Kompressor oder ein Enveloper (z. B. :ref:`ducka`) zum
Einsatz kommen. Wie wird Sidechaining nun verwendet? Zuerst müssen wir wieder
ein paar Verbindungen herstellen. Luppps „sidechain_key“-Anschluss muss an den
Sidechain-Eingang und Luppps „sidechain_signal“-Ausgang an den regulären
Audioeingang von :ref:`ducka` angeschlossen werden. Verbinde außerdem die
Ausgänge des Plugins mit den „return“-Anschlüssen von Luppp.

Zurück zu Luppp. Bei einem Track musst du nun die „Key“-Schaltfläche
aktivieren. Dadurch wird die Ausgabe des Tracks zum Auslöser für den
Sidechain-Effekt. Mit dem Regler über der „Key“-Schaltfläche kannst du nun
jeden Track an das Plugin senden. Wenn du dir ansehen willst, wie das
funktioniert, schaue dir diese Videos an:

* Erklärung: https://www.youtube.com/watch?v=-AwtMUeBc9w
* Showcase: https://www.youtube.com/watch?v=bPJQs6w2XQc

Eingabebereich
==============

Am Anfang dieser Anleitung haben wir eine Audioquelle mit dem „master_in“-Kanal
von Luppp verbunden. Du kannst verschiedene andere Quelle anschließen, jede
Ausgabe eines Mixers oder was auch immer du dir vorstellen kannst! In der Ecke
ganz oben rechts der Oberfläche siehst du den Eingabebereich von Luppp.

.. Tip ::
    Luppp hat nur einen Monoeingang. Wenn du eine Stereoquelle wie einen
    Synthesizer anschließen willst, gibt es mehrere Möglichkeiten. In den
    meisten Fällen reicht es aus, nur einen Kanal zu verbinden, da beide Kanäle
    gleich sind. Wenn du tatsächlich beide Kanäle brauchst, ziehe in betracht,
    sie mit einem Mixer zu mischen. Einfach beide Kanäle an den selben Ausgang
    anzuschließen, könnte zu Problemen führen.

Hier gibt es eine Pegelanzeige und einen Fader zur Anpassung der Lautstärke des
Eingangssignals. Die Regler bewirken folgendes:

.. image:: img/luppp/luppp_inputsection.png
   :align: left

* „Snd“-Schaltfläche aktiviert die „Send“-Funktion
* Der Regler darüber regelt die Stärke, z. B. des Halls
* „Key“-Schaltfläche setzt das Eingangssignal als „Key“-Signal für das Sidechaining
* Der Regler darüber regelt welcher Anteil als Sidechain-Signal verwendet wird
* „Mix“-Schaltfläche aktiviert das Weiterleiten des Eingangssignals zum Masterausgang von Luppp
* Der Regler darüber regelt welcher Anteil zum Masterausgang weitergegeben wird.

Du hast also großartige Möglichkeiten: ein bisschen Hall für den Eingang,
Verwendung eines Eingangssignals für einen speziellen Sidechaining-Key? Kein
Problem! Direkt mit Luppp kannst du hören was du spielst und die
Aufnahmelautstärke an die Lautstärke der anderen Tracks anpassen.

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
