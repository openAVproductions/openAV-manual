########
Luppp
########

.. image:: img/luppp/luppp.png
   :align: center

Luppp est un outil de création musicale, destiné à l’utilisation en direct (live). 
L’objectif principal est le traitement en temps réel ainsi qu’une utilisation rapide et intuitive. 
Avec un support étendu du mappage midi, vous pouvez gérer les boucles comme vous aimez ! 
Les paragraphes suivants vous expliqueront comment connecter Luppp avec Jack pour les entrées et sorties audio et vous présenteront les concepts de "scènes" et de "clips" pour utiliser votre créativité pour des performances en direct !

Luppp et JACK
=============

Si vous débutez avec Jack et Luppp, voici un exemple en vidéo qui vous montre à quoi ressemble une session d’utilisation typique de boucles dans Luppp :
https://www.youtube.com/watch?v=R6WiWDDKRCQ

Avant de pouvoir enregistrer, il faut connecter les sources audio aux entrées principales (master_in_left et master_in_right) de Luppp et connecter les sorties principales (master_left et master_right) aux sorties du système (playback_1 et playback_2). Voir la capture d’écran des connexions :

.. image:: img/luppp/luppp_jack_connections.png
   :align: center

Ensuite, nous jeterons un œil à l'interface de Luppp, qui peut sembler complexe au départ, 
mais qui est vraiment plutôt simple une fois que l'on comprend à quoi sert chaque partie de l'interface graphique.

.. image:: img/luppp/luppp_interface.png
   :align: left

Vous pouvez voir 8 pistes contenant 10 clips chacune. Afin de vérifier que votre configuration fonctionne, 
faites jouer votre source audio et vous devriez voir l'amplitude de l’audio dans le vu-mètre en haut à droite de l’interface. Si cela fonctionne, vous êtes prêt !

Maintenant, cliquez sur un clip pour démarrer l’enregistrement puis cliquez une nouvelle fois 
pour lancer la lecture en boucle ! 
Toutes les actions de Luppp sont synchronisées à la pulsation,
qui est indiqué par les quatre carrés en bas à droite de la fenêtre. 
Vous pouvez changer le tempo en tournant le bouton dans lequel est indiqué le nombre de BPM 
(qui doit être à 120 par défaut).

.. image:: img/luppp/luppp_scenes.png
	:align: right

Scènes 
======

Un concept de Luppp plutôt important est les ‘scènes’. Dans chaque piste, vous pouvez seulement jouer un clip à la fois. 
la section ‘Master’ de Luppp, vous pouvez voir une liste de ’scènes’. Vous pouvez lancer une scène en cliquant dessus. 
Quand vous faites cela, tous les clips de cette ligne commencent en même temps.

.. Tip::
   Quand vous utilisez des clips dont la longueur est supérieur à une mesure, 
   faites attention à démarrer l’enregistrement en même temps que les autres clips de la ligne qui sont lancés. 
   Sinon, lancer une scène créera un peu de désordre ;)

-----

.. image:: img/luppp/luppp_track.png
   :align: left

Pistes
======

Toutes les pistes de Luppp possèdent des contrôleurs faisant des choses incroyables. Nous allons les passer en revue à partir du haut vers le bas. Premièrement, il y a le nom de la piste. Vous pouvez le modifier en cliquant-droit dessus. En dessous, se trouve un cercle affichant la progression de la lecture de la boucle dans la piste. C'est plutôt utile de le regarder lors de l'enregistrement d'autres clips dans la même ligne. La chose suivante est "les clips". Vous pouvez leurs donner un nom avec un clic-droit également. Ils affichent également le statut correct d'un clip, s'il est en train d'enregistrer, d'être lu, ou vide. En bas, il y a un chariot qui ajuste le volume de la piste mixé dans le master. Sur la gauche des chariots, se trouvent certains contrôles que nous décrirons dans les sections suivantes.

.. Tip::
	Vous pouvez utiliser votre clavier alpha-numérique pour contrôler les clips ! 
	La première scène est représentée par les nombres de 1 à 8, le 9 déclenche la première scène.
	Les lignes suivantes sont branchées sur les scènes sous-jacentes. Essayez !

-----

Envoi de réverb'
================

Cette fonctionnalité vous offre la possibilité d'ajouter simplement de la réverbération sur une piste. Avant de pouvoir essayer ceci, nous devons connecter les send_out de Luppp à une réverb' de notre choix (par exemple :ref:`roomy`) et les sorties de la réverb' en retour dans les master_returns de Luppp. Lorsque c'est fait, nous pouvons activer la réverb' pour chaque piste avec le bouton Snd-Button et ajuster la quantité de réverb' avec le bouton rotatif au dessus.

Les connexions pour un envoi de réverb' sont comme suit :

.. image:: img/luppp/luppp_reverb_send_connections.png
   :align: center

.. image:: img/luppp/luppp_reverb_roomy.png
   :align: right

Et les paramètres recommandés pour Roomy sont affichés ici - la partie la plus importante est de paramétrer le bouton Dry/Wet (original/traité) à 100% Wet, ainsi seule la réverb' ressort, et le signal original est complètement mis en sourdine. 
Étant donné que Luppp sort déjà le signal original, nous ne voulons pas que la réverb' le fasse aussi !

Il y a une vidéo (en anglais) à ce sujet: https://www.youtube.com/watch?v=wLy9oG_WpHg

-----

Chaînage latéral
================

Il est très facile de pratiquer un chaînage latéral (NdT : "sidechaining" en anglais) en utilisant Luppp, 
par exemple pour créer des lignes de basse house. Le concept est plutôt simple : vous utilisez un signal audio pour contrôler le traitement d'un autre signal. 
Ce traitement peut être un compresseur ou un enveloppeur (par exemple : ref:ducka). Alors, comment l'utiliser ?
Premièrement, nous devons ici aussi faire des connexions. Les sidechain_key de Luppp doivent être connectés à une entrée de chaînage latéral et les sidechain_signal de Luppp doivent être connectés aux entrées audio régulières du greffon Ducka. 
Envoyez les sorties des greffons aux sorties master.

Retour à Luppp. Sur une piste, vous devez activer le bouton "Key". Ce faisant, la sortie de la piste est le déclencheur de l'effet de chaînage latéral. Maintenant, vous pouvez envoyer chaque piste avec le bouton rotatif au dessus du bouton "Key" 
vers le greffon. Si vous souhaitez voir comment ceci fonctionne, regardez ces vidéos (en anglais) : 

* Explication: https://www.youtube.com/watch?v=-AwtMUeBc9w
* Démonstration: https://www.youtube.com/watch?v=bPJQs6w2XQc

La section d'entrée
===================

Au début de ce tutoriel, nous avons connecté une source audio aux master_in de Luppp. 
Vous pouvez connecter plusieurs entrées de differentes sources, ou chaque sortie d'un mixeur, ou tout ce que pouvez imaginer ! Dans le coin droit supérieur de l'interface, vous pouvez voir la section d'entrée de Luppp.

Ici, vous avez un vu-mètre, et un chariot pour ajuster le volume des entrées. 
Les boutons en dessous font les choses suivantes :

.. image:: img/luppp/luppp_inputsection.png
   :align: left

* le bouton "Snd" active l'envoi (le bouton ci-dessus dose la quantité, comme la réverb') 
* le bouton "Key" défini les entrées comme signal source pour le chaînage latéral 
* le bouton au dessus du bouton "Key" règle la quantité de signal pour le chaînage latéral
* le bouton "Mix" active le routage des entrées vers les sorties principales de Luppp 
* le bouton au dessus du bouton "Mix" règle la quantité de signal des entrées dans les sorties principales 

Vous avez donc de grandes possibilités : une petite réverb' sur les entrées, utiliser des entrées pour un chaînage latéral special ? Facile! Vous pouvez surveiller ce que vous jouez avec Luppp et ajuster le volume enregistré 
pour l'adapter aux autres pistes.

La section Master
=================

.. image:: img/luppp/luppp_master_section.png
   :align: right

Jetez un oeil à la dernière partie de l'interface : la section master. 
Les fonctions de la plupart des éléments sont vraiment évidents, donc je les expliquerai rapidement :

* les carrés vert, jaune, orange et rouge montrent le battement (de bas en haut) 
* le bouton "Stop/Play" arrête ou redémarre la lecture 
* avec le bouton "Tap", vous pouvez ajuster le tempo en cliquant la pulsation 
* le bouton "Metro" active le métronome dans les sorties casque (headphones_out) de Luppp 
(notez que vous pouvez choisir entre une sélection de différents niveaux de volume en cliquant-droit sur le bouton "Metro") 
* le bouton avec les chiffres indique le tempo 
* le bouton "Return" ajuste le volume du retour audio (comme la réverb')
* le chariot ajuste le volume principal. 

Configuration
=============

Luppp fournit quelques fonctionnalités de configuration dans un fichier se trouvant dans le répertoire de configuration de l'utilisateur. Il permet de mettre des contrôleurs par défaut en les ajoutant à la liste des contrôleurs par défaut, comme indiqué ci dessous. Notez bien que plusieurs contrôleurs peuvent être ajoutés, listés comme des shaines séparées avec une virgule intercalée entre eux.

Le fichier à éditer es:
``~/.config/openAV/luppp/luppp.prfs``

notamment, mettez à jour cette ligne qui contient  le nom du fichier de votre contrôleur par défaut :
``"defaultControllers":   ["akai_apc.ctlr"],``
