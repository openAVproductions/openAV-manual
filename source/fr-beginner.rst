
.. _beginner_setup:

###############
Pour les débutants
###############

Bienvenue dans le monde merveilleux de l'audio sous Linux ! Bien que l'audio
avec Linux en général soit techniquement un peu plus exigeant 
pour les musiciens, il y a de gros d'avantages lorsque l'on comprend
la technologie que l'on utilise, et en l'adaptant exactement à ce que
vous voulez.
Les logiciels OpenAV *vous* ciblent (vous, le musicien jouant en live)
et si vous avez des retours à faire, n'hésitez pas `à nous contacter`_ (lien en anglais) !

.. _à nous contacter: http://openavproductions.com/contact/

Cette page présente au débutant la façon d'utiliser les logiciels
OpenAV, de configurer Jack, de lancer des greffons LV2 avec Jalv, et
répond à d'autres questions courantes.

.. _lv2_plugin:

Greffons LV2
==========

Les greffons LV2 sont des extensions dédiées aux applications audio.
Chaque greffon contient une (ou des) fonctionnalité mise à
disposition lorsque le greffon est chargé par un programme hôte.
LV2 est une interface de programmation applicative (API) de greffons
à source ouverte, ce qui veut dire qu'il peut être utilisé gratuitement par
tout le monde, ni contrat et ni copyright propriétaire ici !

OpenAV fabrique des greffons LV2, la spécification du greffon LV2 étant très
puissante, flexible et extensible. Cela permet à OpenAV de créer des greffons
complexes comme des échantillonneurs et synthétiseurs, utilisés facilement
dans des stations de travail audionumériques (STAN ou DAW) telles que Ardour, Audacity
et bien d'autres !

Pour lister la liste des greffons installés sur votre système, lancez
la commande suivante dans un terminal : ``lv2ls``. Le résultat est une
longue liste d'URI, qui identifient chaque greffon disponible sur
votre système. Ces URI seront utilisés dans la section
:ref:`launching_a_plugin`. Un exemple d'URI est
``http://www.openavproductions.com/artyfx#roomy``.

Pour accéder à d'avantages d'informations (techniques) à propos d'un greffon LV2,
vous pouvez lancer la commande ``lv2info`` avec l'URI du greffon en
argument. Voilà par exemple le résultat pour :ref:`Roomy` :

.. literalinclude:: cmdoutput/lv2ls_roomy.txt

.. _jack:

JACK
====

JACK est un programme vous permettant de faire fonctionner des applications
audio ainsi que de rediriger les flux audio entre elles. Ici, à OpenAV JACK,
nous avons *toujours* un JACK qui tourne lors du développement des logiciels
(c'est la colonne vertébrale de l'audio sous Linux), alors habituez-vous !

.. _starting_jack:

Démarrer JACK
-------------

En ligne de commande
~~~~~~~~~~~~~~~~~~~~
Pour avoir un contrôle total de votre configuration audio, lancez JACK
en ligne de commande. Cela peut sembler exagéré, mais OpenAV vous assure
que cela vous évitera de nombreux maux de tête. Vous pouvez aller
directement à :ref:`QJackCtl` si vous voulez utiliser une interface
graphique.

La commande suivante devrait (à priori) correctement fonctionner,
essayez là :

``jackd -P 85 -dalsa -dhw:0 -r48000 -p128 -n 2 -Xseq``

Voilà le résultat que vous devriez avoir ::

  JACK compiled with System V SHM support.
  loading driver ..
  apparent rate = 48000
  creating alsa driver ... hw:0|hw:0|128|2|48000|0|0|nomon|swmeter|-|32bit
  configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
  ALSA: final selected sample format for capture: 32bit integer little-endian
  ALSA: use 2 periods for capture
  ALSA: final selected sample format for playback: 32bit integer little-endian
  ALSA: use 2 periods for playback
  creating alsa_midi driver ...

OK, JACK est maintenant lancé, si rien de plus ne s'affiche, nous sommes prêts !
Ceci dit, JACK affichera parfois des ::

  **** alsa_pcm: xrun of at least 213428.124 msecs

Cela signifie que l'ordinateur n'arrive pas à suivre (souvent un signe qu'il
doit être configuré pour `l'audio temps-réel
<http://openavproductions.com/real-time-latency-tuning/>`_, ou bien, s'il est vieux
de plus de 15 ans, peut être qu'il n'est simplement pas assez rapide).

.. _qjackctl:

QJackCtl
~~~~~~~~
Si vous voulez utiliser un programme avec interface graphique pour configurer et démarrer
JACK, QJackCtl fera exactement cela pour vous. Un tutoriel de démarrage est proposé
sur `le site de LinuxMAO.org <http://linuxmao.org/Jack+premier+lancement>`_.

.. _jalv:

JALV
====
JALV est un petit outil permettant de charger un greffon LV2 ,et le lancer
avec JACK. Il est très utile pour lancer un greffon OpenAV comme si c'était
un programme autonome, et communiquant nativement avec JACK. La section
:ref:`launching_a_plugin` explique commment lancer des greffons avec JALV.
     
.. _launching_a_plugin:

Lancer un greffon LV2
=======================

Cette section vous explique comment lancer un greffon en utilisant JACK
comme moteur audio et Jalv pour héberger les greffons LV2.
Les greffons LV2 sont identifiés par des URI, voir la section
:ref:`lv2_plugin` afin d'obtenir la liste des greffons installés.

* Démarrez JACK. Si vous n'avez jamais démarré JACK auparavant, voir la section :ref:`starting_jack`.
* Lancez Roomy dans JALV en utilisant la commande suivante : ``jalv.gtk http://www.openavproductions.com/artyfx#roomy``
* Utilisez :ref:`qjackctl` afin de connecter le ``System:capture`` à ``Roomy:in``, et ``Roomy:out`` à ``System:playback``.

Et voilà ! Tout son capturé par l'interface-son matérielle passera à travers 
l'effet :ref:`Roomy`, puis sera joué par les haut-parleurs.
