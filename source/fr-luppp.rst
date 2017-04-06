########
Luppp
########

.. image:: img/luppp/luppp.png
   :align: center

Luppp est un outil de création musicale, destiné à l’utilisation en direct (live).
L’objectif principal est le traitement en temps réel ainsi qu’une utilisation rapide et intuitive.
Avec un support étendu du mappage midi, vous pouvez gérer les boucles comme vous aimez !
Les paragraphes suivants vous expliqueront comment connecter Luppp avec Jack pour les entrées et sorties audio
et vous présenteront les concepts de "scènes" et de "clips" pour utiliser votre créativité pour des performances en direct !

Luppp et JACK
==============

Si vous débutez avec Jack et Luppp, voici un exemple en vidéo qui vous montre
à quoi ressemble une session d’utilisation typique de boucles dans Luppp :
https://www.youtube.com/watch?v=R6WiWDDKRCQ

Avant de pouvoir enregistrer, il faut connecter les sources audio à l’entrée principale
(master_in) de Luppp et connecter les sorties principales (master_left et master_right)
aux sorties du système (playback_1  et playback_2). Voir la capture d’écran des connexions :

.. image:: img/luppp/luppp_jack_connections.png
   :align: center


Ensuite, nous jeterons un œil à l'interface de Luppp, qui peut sembler complexe au
départ, mais qui est vraiment plutôt simple une fois que l'on comprend à quoi sert
chaque partie de l'interface graphique.

.. image:: img/luppp/luppp_interface.png
   :align: left

Vous pouvez voir 8 pistes contenant 10 clips chacune. Afin de vérifier que votre configuration fonctionne,
faites jouer votre source audio et vous devriez voir l'amplitude de l’audio
dans le vu-mètre en haut à droite de l’interface. Si cela fonctionne, vous êtes prêt !

Maintenant, cliquez sur un clip pour démarrer l’enregistrement puis cliquez une nouvelle fois pour lancer la lecture en boucle !
Toutes les actions de Luppp sont synchronisées à la pulsation, qui est indiqué par les quatre carrés en bas à droite de la fenêtre. 
Vous pouvez changer le tempo en tournant le bouton dans lequel est indiqué le nombre de BPM (qui doit être à 120 par défaut).


.. image:: img/luppp/luppp_scenes.png
	:align: right

Scènes 
======

Un concept de Luppp plutôt important est les ‘scènes’. Dans chaque piste, vous pouvez seulement jouer un clip à la fois.
Dans la section ‘Master’ de Luppp, vous pouvez voir une liste de ’scènes’. Vous pouvez lancer une scène en cliquant dessus.
Quand vous faites cela, tous les clips de cette ligne commencent en même temps.

.. Astuce::
   Quand vous utilisez des clips dont la longueur est supérieur à une mesure, 
   faites attention à démarrer l’enregistrement en même temps que les autres clips 
   de la ligne qui sont lancés. Sinon, lancer une scène créera un peu de désordre ;)


-----

.. image:: img/luppp/luppp_track.png
   :align: left

Pistes
======

Toutes les pistes de Luppp possèdent des contrôleurs faisant des choses incroyables.
Nous allons les passer en revue à partir du haut vers le bas.
Premièrement, il y a le nom de la piste. Vous pouvez le modifier en cliquant-droit dessus.
En dessous, se trouve un cercle affichant la progression de la lecture de la boucle dans la piste.
C'est plutôt utile de le regarder lors de l'enregistrement d'autres clips dans la même ligne.
La chose suivante est "les clips". Vous pouvez leurs donner un nom avec un clic-droit également.
Ils affichent également le statut correct d'un clip, s'il est en train d'enregistrer, d'être lu, ou vide.
En bas, il y a un chariot qui ajuste le volume de la piste mixé dans le master.
Sur la gauche des chariots, se trouvent certains contrôles que nous décrirons dans les sections suivantes.

.. Tip::
	Vous pouvez utiliser votre clavier alpha-numérique pour contrôler les clips !
	La première scène est représentée par les nombres de 1 à 8, le 9 déclenche la première scène.
	Les lignes suivantes sont branchées sur les scènes sous-jacentes. Essayez !

-----

Envoi de réverb'
================

Cette fonctionnalité vous offre la possibilité d'ajouter simplement de la réverbération sur une piste.
Avant de pouvoir essayer ceci, nous devons connecter les send_out de Luppp à une réverb' de notre choix
(par exemple :ref:`roomy`) et les sorties de la réverb' en retour dans les master_returns de Luppp.
Lorsque c'est fait, nous pouvons activer la réverb' pour chaque piste avec le bouton Snd-Button et
ajuster la quantité de réverb' avec le bouton rotatif au dessus.

Les connexions pour un envoi de réverb' sont comme suit :

.. image:: img/luppp/luppp_reverb_send_connections.png
   :align: center

.. image:: img/luppp/luppp_reverb_roomy.png
   :align: right

Et les paramètres recommandés pour Roomy sont affichés ici - la partie la plus importante
est de paramétrer le bouton Dry/Wet (original/traité) à 100% Wet, ainsi seule la réverb' ressort,
et le signal original est complètement mis en sourdine. Étant donné que Luppp sort déjà le signal original,
nous ne voulons pas que la réverb' le fasse aussi !

Il y a une vidéo (en anglais) à ce sujet : https://www.youtube.com/watch?v=wLy9oG_WpHg

-----

Sidechaining
============

Using Luppp its very easy to use sidechaining, for example to create some
house bass lines.. Its a pretty simple concept: you use one audio signal to
control the processing of another signal. This processing could be a
compressor or an enveloper (eg :ref:`ducka`). So, how to use it? At first
we again need to do some connections. Luppps sidechain_key needs to be
connected to a sidechain input and Luppps sidechain_signal needs to be
connected to the regular audio inputs of the Ducka plugin.
Send the outputs of the plugins to the master outputs.

Back to Luppp. On one track you need to enable the Key-Button. This way the
output of the track is the trigger for the sidechain effect. Now you can
send each track with the knob above the Key-Button to the plugin. If you
want to see how its works, watch these videos: 

* Explanation: https://www.youtube.com/watch?v=-AwtMUeBc9w
* Showcase: https://www.youtube.com/watch?v=bPJQs6w2XQc

Input Section
=============

At the beginning of this tutorial we connected a audio source to Luppps master_in. 
You can input several different sources, or any output of a mixer or what ever you can 
imagine! In the top right corner of the GUI you can see the Luppp Input Section.

.. Tip ::
	Luppp only has a mono input. If you want to connect a stereo source like a synthesizer, 
	there are severel possibilities. In the most cases its enough to connect just one side since 
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

Configuration
=============

Luppp provides some configuration features in a file under the user's
config directory. It allows setting default controllers by adding them
to the default controllers list, as shown below. Note that multiple
controllers can be added, listed as seperate strings with a comma
inbetween.

The file to edit is:
``~/.config/openAV/luppp/luppp.prfs``
in particular, update this line to contain the filename of your default
controllers:
``"defaultControllers":   ["akai_apc.ctlr"],``
