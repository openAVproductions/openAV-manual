
.. _beginner_setup:

###############
Pour les débutants
###############

Bienvenue dans le monde excitant de l'Audio sous Linux ! Bien que l'audio
avec Linux soit en général un peu plus exigeant d'un point de vue technique
pour les musiciens, il y a beaucoup à apprendre lorsque l'on comprend
la technologie que l'on utilise. En outre pouvoir
adapter la technologie à ce qu'on veut est un avantage important.
Les logiciels OpenAV *vous* ciblent (vous, le musicien jouant en live)
et si vous avez des retours à faire, n'hésitez pas `à nous contacter`_ !

.. _à nous contacter: http://openavproductions.com/contact/

Cette page présente aux débutants comment utiliser les logiciels
OpenAV, comment configurer Jack, lancer des greffons LV2 avec Jalv et
répond à d'autres questions courantes.

.. _lv2_plugin:

Greffons LV2
==========

Les greffons LV2 sont des extensions dédiées aux applications audio.
Chaque greffon contient une fonctionnalité (voire plusieurs) mise à
disposition lorsque le greffon est chargé par un programme dédié.
LV2 est une interface de programmation applicative (API) de greffons
open source, ce qui veut dire qu'il peut être utilisé gratuitement par
tout le monde, ni contrats et ni copyrights ici !

OpenAV a créé des greffons LV2, car la spécification du greffon LV2 est très
puissante, flexible et extensible. Cela permet à OpenAv de créer des greffons
complexes comme des échantillons musicaux et synthés, utilisés facilement
dans des stations audionumériques (DAWs) tel que Ardour, Audacity et bien
d'autres !

Pour lister la liste des greffons installés sur votre système, lancez
la commande suivante dans un terminal : ``lv2ls``. Le résultat est une
longue liste d'URIs, qui identifient chaque greffon disponibles sur
votre système. Ces URIs seront utilisés dans la section
:ref:`launching_a_plugin`. Un exemple d'URI est
``http://www.openavproductions.com/artyfx#roomy``.

Pour accéder à plus d'informations (techniques) à propos d'un greffon LV2,
vous pouvez lancer la commande ``lv2info`` avec l'URI du greffon en
argument. Voilà par exemple le résultat pour :ref:`Roomy` :

.. literalinclude:: cmdoutput/lv2ls_roomy.txt

.. _jack:

JACK
====

JACK est un programme permettant de lancer des applications audio ainsi que
de rediriger les flux audio entre eux. Ici à OpenAV JACK est tourne
*toujours* lors du développement des logiciels (c'est la colonne
vertébrale de l'audio sous Linux), alors habituez vous !

.. _starting_jack:

Démarrer JACK
-------------

En lignes de commande
~~~~~~~~~~~~~~~~~~~~~
Pour avoir un contrôle total de votre configuration audio, lancez JACK
en ligne de commande. Même si cela semble être exagéré, OpenAV vous assure
que cela vous évitera de nombreux mals de tête. Vous pouvez aller
directement à :ref:`QJackCtl` si vous voulez utiliser une interface
graphique.

La commande suivante devrait (a priori) parfaitement fonctionner,
essayez là :

``jackd -P 85 -dalsa -dhw:0 -r48000 -p128 -n 2 -Xseq``

Voilà le résultat que vous devriez avoir::

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

JACK est maintenant lancé, si rien de plus ne s'affiche nous sommes prêts !
Néanmoins parfois JACK affichera des::

  **** alsa_pcm: xrun of at least 213428.124 msecs

Cela signifie que l'ordinateur n'arrive pas à suivre (souvent un signe qu'il
doit être configuré pour `l'audio à temps réel
<http://openavproductions.com/real-time-latency-tuning/>`_, ou bien juste
qu'il est vieux de 15 ans et qu'il n'est pas assez rapide).

.. _qjackctl:

QJackCtl
~~~~~~~~
Si vous voulez utiliser un programme graphique pour configurer et démarrer
JACK, orientez-vous vers QJackCtl. Un tutoriel de démarrage est proposé
sur le site `LinuxMAO.fr <http://linuxmao.org/Jack+premier+lancement?structure=Accueil+Tutos>`_.

.. _jalv:

JALV
====
JALV est un petit outil permettant de charger un greffon LV2 et le lancer
avec JACK. Il est utile pour lancer un greffon OpenAV en tant que programme
autonome, communiquant nativement avec JACK. La section
:ref:`launching_a_plugin` explique commment lancer des greffons avec JALV.
     
.. _launching_a_plugin:

Lancer un greffon LV2
=======================

Cette section vous montre comment lancer un greffon en utilisant JACK
comme gestionnaire audio et Jalv pour accueillir les greffons LV2.
Les greffons LV2 sont identifiés par des URIs, voir la section
:ref:`lv2_plugin` afin d'obtenir la liste des greffons installés.

* Démarrez JACK (voir la section :ref:`starting_jack` si vous n'avez jamais
ouvert JACK avant).
* Lancez Roomy dans JALV en utilisant la commande suivante :
``jalv.gtk http://www.openavproductions.com/artyfx#roomy``
* Utilisez :ref:`qjackctl` afin de connecter le ``System:capture`` à
``Roomy:in`` et ``Roomy:out`` à ``System:playback``.

Et voilà ! Tous les sons capturés par la carte graphique seront affectés
par l'effet :ref:`Roomy` et seront joués par les haut parleurs.
