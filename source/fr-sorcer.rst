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

Crénelage (Aliasing) et artefacts
---------------------------------
Veuillez noter que généralement, la synthèse par table d'onde engendre des
effets de bords. Jouer un échantillon à un taux différent (altérant la vitesse)
crée des artefacts. Avec des taux de lecture proches de :abbr:`unity(The playback rate of 1,
also the original playback rate)` ces artefacts peuvent être audibles à moins que de
l':abbr:`interpolation(smoothing of audio data based on the
playback rate)` soit réalisée.

Le crénelage peut être évité par de l'interpolation, ou précautionneusement
en pré-traitant la forme d'onde enregistrée. Plus la hauteur augmente, plus
les harmoniques peuvent petre retirés du signal, ce qui évite le crénelage.
Dans son état actuel, Sorcer ne fait ni d'interpolation de la forme d'onde,
ni du pré-traitement de la forme d'onde.

Pourquoi ne pas simplement corriger le crénelage ?
--------------------------------------------------
Bien que ce soit possible à ajouter, ceci modifierait la sonorité de Sorcer,
et modifierait tout morceau ayant été écrit. Pour cette raison, Sorcer ne
verra aucune amélioration de son moteur de lecture mais, n'ayez crainte,
OpenAV a des plans pour sortir des nouveaux synthétiseurs dans le futur, avec
de l'annulation de crénelage, et des modulations avec encore plus de possibilité
que Sorcer n'a jamais eu !

____

.. image:: img/sorcer/sorcer_lfo_remove.png
   :align: right


Enveloppes et modulation
========================
Sorcer possède également des fonctionnalités d'enveloppe et de modulation,
un LFO peut moduler le filtre et les tables d'onde, alors qu'un ADSR permet
le contrôle du volume par note. Regardons ces parties en détails.

LFO
---

La section LFO possède 4 contrôles :
 * W1
 * W2
 * Speed
 * Amp
La vitesse et l'amplitude du LFO lui-même sont contrôlés par les boutons Speed
et Amp. Les boutons W1 et W2 contrôlent la *quantité* du signal LFO qui
doit être utilisée pour moduler les positions horizontales Wave1 ou Wave2.
Ceci est très utile pour créer des sons de dubstep-bass bougeant constamment !

Remove
------
La section "remove" contient un filtre passe-bas avec un bouton de coupure,
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
L'ADSR fourni les touches finales sur le son - les valeurs par défaut fournissent
un mur de son mais, ajoutez un fondu à l'ouverture et un peu de déclin, et vous
aurez construit des sons ressemblant à un pad.

Master
------
La section master fournie un compresseur avec gain, seuil (NdT : "threshold"), attaque
et relâche (NdT : release). Un chariot de volume-master permet d'apprivoiser Sorcer pour
le garder en place dans le mix.

Conclusion
==========

Ceci était un tour rapide en coup de vent du synthétiseur Sorcer qui, bien qu'étant limité
dans ses objectifs, est un bon synthétiseur pour démarrer son utilisation pour créer des
lignes de basse, et comprendre le fonctionnement du routage à l'intérieur d'un synthétiseur.
Bien sûr, pour une ligne de basse modulée de gros dubstep, Sorcer est le moyen le plus simple
d'obtenir une super grosse sub-basse aussi !
