.. image:: img/sorcer/sorcer.png
   :align: right
   :scale: 60 %

########
Sorcer
########

Sorcer est un synthétiseur polyphonique par table d'onde au format LV2.
Son empreinte sonore est l'une des infra-basses modulées rugueusement,
conduite par un mur de son. Deux oscillateurs transformés par table
d'onde et un oscillateur sinusoïdal fournissent les routines de génération.
Le LFO peut être relié à la modulation de table d'onde, et aussi au filtre
de coupure. Un ADSR permet de dessiner les contours du son 
résultant, pendant qu'un volume général termine la chaîne de traitement.
Vous pouvez facilement créer une variété de lignes de basse de dubstep,
et des sons de pad rugueux. 

.. note:: Le code source est disponible sur la `page Sorcer sur Github`_
	mais votre gestionnaire de paquet possède probablement une version pré-compilée !

.. _page Sorcer sur Github: https://github.com/openAVproductions/openAV-Sorcer/

____

.. image:: img/sorcer/sorcer_osc.png
   :align: right

Oscillateurs
============

Les oscillateurs sont les générateurs de son de la plupart des synthétiseurs -
Sorcer n'est pas différent. Sorcer possède 3 oscillateurs, deux osccillateurs
"Wave" qui utilisent des tables d'onde pour générer l'audio, et un oscillateur
à onde sinusodale "Sub-Bass".

Les oscillateurs "Wave" permettent un affaiblissement entre deux timbres en
déplaçant le pad X/Y sur la direction horizontale. Le déplacer verticallement
modifie le volume de l'oscillateur. L'oscillateur sub-bass possède seulement
un volume - il joue toujours une onde sinusoïdale, puisque c'est la fréquence
la plus basse possible.

Tables d'onde
-------------
Les tables d'ondes sont des enregistrements courts d'un son de cycle-unique.
Ceci permet au synthétiseur de jouer de manière répétée le même cycle d'audio,
et crée une tonalité continue possèdant un timbre spécifique dû aux harmoniques
dans l'audio enregistré.

Sorcer possède quatre enregistrement de table d'onde; et en utilise deux par
osciallateur de table d'onde. Les enregistrements sont choisis avec soin pour
avoir des caractéristiques de son similaires qui lorsqu'ils sont affaiblis,
provoque alors une belle transition spectrale.

Aliasing and Artifacts
----------------------
Note that wavetable synthesis generally has some side effects. Playing a
sample back at a different rate (altering the speed) creates some
artifacts. With playback rates close to :abbr:`unity(The playback rate of 1,
also the original playback rate)` these artifacts can be audible unless
some :abbr:`interpolation(smoothing of audio data based on the
playback rate)` is done.

Aliasing can be avoided by interpolation, or careful pre-processing of
the recorded waveform. As pitch goes up harmonics can be removed from the
signal, which avoids aliasing. In its current state, Sorcer does not do
either of interpolation of the waveform or pre-processing of the waveform.

Why not just fix the Aliasing?
------------------------------
Although possible to add, it would change the sound of Sorcer - and change
any existing songs that have written. For that reason, Sorcer will not see
any improvements in its playback engine - but fear not - OpenAV has plans
to release new synths in the future with alias-avoidance and more capable
modulation than Sorcer ever had!

____

.. image:: img/sorcer/sorcer_lfo_remove.png
   :align: right


Enveloppes et modulation
========================
Sorcer possède également des fonctionnalités d'enveloppe et de modulation,
un LFO peut moduler le filtre et les tables d'onde, alors qu'un ADSR permet
le contrôle le volume par note. Regardons ces parties en détails.

LFO
---

La section LFO possède 4 contrôles :
 * W1
 * W2
 * Speed
 * Amp
La vitesse et l'amplitude du LFO lui-même est contrôlé par les boutons Speed
et Amp. Les boutons W1 et W2 contrôlent la *quantité* du signal LFO qui
doit être utilisée pour moduler les positions horizontales Wave1 ou Wave2.
Ceci est très utile pour créer des sons de dubstep-bass bougeant constamment !

Remove
------
La section "remove" contient un filtre passe-bas avec un bouton de coupure cutoff,
et un bouton de modulation. Le bouton de coupure (NdT : "cutoff") paramètre une
valeur statique pour le filtre passe-bas - utile pour étouffer le son basse et
laisser de la place dans le mix pour d'autres instruments. Pour ajouter davantage
d'énergie au mix, augmenter le bouton de modulation pour modifier le Cutoff par la
sortie du LFO.

____

.. image:: img/sorcer/sorcer_adsr_master.png
   :align: right

ADSR
----
The ADSR provides the final touches on the sound - the defaults provide a
wall of sound, but add a fade in and some decay to build pad-like sounds..

Master
------
The master section provides a compressor with Gain, Threshold, Attack and
Release. A master-volume slider allows taming Sorcer to keep it in its
place in the mix.

Conclusion
==========

That was a whirlwind fast tour of the Sorcer synth - although its limited
in its scope, it is a good synth to start using for basslines, and
understand the way routing inside a synthesizer works. Of course, for a
heavy dubstep modulated bassline, Sorcer is the easiest way to get that
super heavy sub-bass too!
