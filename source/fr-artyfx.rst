
.. _artyfx:

########
ArtyFX
########

ArtyFX est une suite d’effets audio, qui peuvent être utilisés de manière autonome mais qui sont aussi conçus pour être insérés dans d’autres applications plus complexes d’OpenAV comme Fabla2,Sorcer and Luppp. Chaque effet peut être utilisé individuellement comme greffon LV2.

ArtyFX comprend différents greffons – tous les effets classiques comme les réverbes, delays et filtres sont inclus. Les paragraphes suivants détaillent chaque greffon individuellement, montrant comment ils peuvent être utilisés, et faisant aussi quelques suggestions sur les meilleures utilisations.

Vous avez des suggestions de greffons pour les ArtyFx? Contactez OpenAV !


____

.. image:: img/artyfx/artyfx_bitta.*
  :align: right
.. _bitta:

Bitta
=======
Bitta est un greffon de réduction de bits (bit-crusher). L’écrasement de bits réduit la résolution du signal audio. Veuillez noter que l'écrasement de bit est un traitement qui dépend du volume du signal et donc, vérifiez que vos volumes sont corrects ! Les signaux calmes sont transformés en silence lorsqu'ils sont écrasés. 
* Crush (écrasement) : modifie la quantité de bits à laquelle l'audio est réduite. 
  

____

.. image:: img/artyfx/artyfx_della.*
  :align: left

.. _della:

Della
=======
Della est un delay se synchronisant sur les BPM, avec des contrôles pour le Retour et le Volume du delay.
* Feedback (retour) : contrôle la quantité de signal qui est réinjecté dans le délai en ligne : augmentez-le pour obtenir un écho-dub-reggae-foufou qui ne s'arrête jamais !
* Volume : modifie la quantité du signal délayé que vous entendez : utile pour conserver les délais en arrière-plan d'une piste.
* Time (temps) : modifie la longueur du délai. Veuillez noter que ceci est “quantifié” en multiple du BPM et donc, il “saute” entre une durée de croche, de noire, de blanche, et de ronde. Della prend la valeur de BPM à partir du programme hôte et donc, si vous modifiez le tempo, il restera en synchronisation !


____

.. image:: img/artyfx/artyfx_ducka.*
  :align: right

.. _ducka:

Ducka
=======
Ducka est un éditeur d'enveloppe avec volume par chaîne latérale : c'est un greffon très utile pour créer des lignes de basse 
qui “pompent” comme dans la musique “house minimale”. Le greffon fonctionne en analysant le volume de l'entrée par chaîne latérale, et modifie le volume d'un piste stéréo séparée en se bansant sur l'amplitude de l'entrée par chaîne latérale. 
* Treshold (seuil) : paramètre le niveau que l'entrée audio doit atteindre pour que la piste stéréo soit réduite.
* Drop (chute) : contrôle la quantité de réduction de volume qui est appliqué.
* Time (temps) : contrôle la quantité de temps que cela prend avant que la piste stéréo ne soit de nouveau fondue. Veuillez noter que ce contrôle dépend du BPM, et que le centre est directement sur les pulsations-off. Un paramètre de la moitié (ce qui est le défaut) est généralement assez musical :)


____

.. image:: img/artyfx/artyfx_driva.*
  :align: left

.. _driva:

Driva
=======
Driva est un effet de multi-distortion capable des plus moyennes distortions comme des plus granuleuses.
* Tone (tonalité) : cliquer sur ce bouton permet de choisir un modèle de distorsion parmi une liste. Choisissez la distortion désirée et éclatez vous. Le bouton “Cancel” (Annuler) en bas de la liste permet de sortir de ce menu sans effectuer de modification.  
* Amount (quantité) : ajuste la quantité de gain / distorsion ajoutée. À utiliser à vos propres risques et périls !


____

.. image:: img/artyfx/artyfx_filta.*
  :align: right

.. _filta:

Filta
=======
Filta est une combinaison de filtres passe-bas et passe-haut. Il est utile pour supprimer les fréquences hautes et basses indésirables de nombreux enregistrements et/ou instruments.
* Frequency (fréquence) : contrôle le type de filtrage étant réalisé, et à quelle fréquence il l'est. Les valeurs plus basses forment un filtre passe-bas. Augmenter le bouton en fait un filtre passe-haut.


____

.. image:: img/artyfx/artyfx_kuiza.*
  :align: left

.. _kuiza:

Kuiza
=======
Kuiza est un égaliseur à 4 bandes. Il est parfait pour modeler créativement le son d'un instrument ou d'un synthétiseur. Chacun des contrôles change l'amplitude à la fréquence donnée. Le gain général peut être utilsé pour réduire ou augmenter le volume général si besoin. Les contrôles (de gauche à droite) :
* Low (grave)  (   ~55 Hz)
* Low mid (bas-médium)  (  ~220 Hz)
* High mid (haut-médium) ( ~1760 Hz)
* High (aigu)    ( ~7040 Hz)
* Gain


____

.. image:: img/artyfx/artyfx_masha.*
  :align: right

.. _masha:

Masha
=======
Masha est un broyeur de rythme. Il enregistre un segment d'audio et le joue ensuite comme une boucle, provoquant ainsi un effet de “bégaiement”.
* Volume modifie la sonie de la boucle de bégaiement. 
* Pass : (passthru) permet de faire déteindre le signal normal à travers.
* Time (temps) : contrôle dépendant du BPM. Il modifie l'enregistrement de la boucle et la longueur de sa lecture. Vous pouvez réduire graduellement cette valeur pour obtenir l'effet “standard” de bégaiement de DJ !


____

.. image:: img/artyfx/artyfx_panda.*
  :align: left

.. _panda:

Panda
=======
Panda est une combinaison d'un compresseur et d'un expandeur combo, avec contôles d'attaque et de relâchement. 
* Threshold (seuil) : le point de passage entre la compression et l'expansion. Les valeurs faibles en font un expandeur, les valeurs hautes un compresseur.
* Release (relâchement) : modifie le temps pour que le greffon fonde en fermeture sa compression/expansion.
* Factor (facteur) : contrôle la quantité de compression/expansion réalisée, aussi connu en tant que bouton de “maximisation”.


____

.. image:: img/artyfx/artyfx_roomy.*
  :align: right

.. _roomy:

Roomy
=======
Roomy est une réverbe spacieuse et douce.

* Time (temps) : modifie la longueur de la queue de réverbération. Des valeurs élevées créeront un mixage plus large et spacieux.
* Damping (étouffement) contrôle l'étouffement des hautes-fréquences : des paramètres bas fournissent un son ouvert et spatieux, alors que des paramètres hauts sont ressentis petits et proches.
* Dry/Wet (original/traité) : modifie la quantité du signal réverbéré mixé en sortie. Utile pour les effets de “construction de réverbération” de trance et de techno… jouez avec !


____

.. image:: img/artyfx/artyfx_satma.*
  :align: left

.. _satma:

Satma
=======
Satma effet fou de distortion. Très utile pour salir l'audio en le rendant granuleux.
* Distortion (distorsion) : modifie la quantité de lise-en-forme du signal qui advient : la quantité général de bruit produite.
* Tone (tonalité) : varie subtilement entre les hautes et les basses fréquences, ou les rend toutes deux granuleuses.


____

.. image:: img/artyfx/artyfx_vihda.*
  :align: right

.. _vihda:

Vihda
=======
Vihda est un réhausseur stéréo, utilisant une matrice “mid-side”. 
* Width (largeur) : affecte la quantité de contenu stéréo dans le signal. Veuillez noter que la technique “mid-side” réhausse uniquement la stéréo, elle ne la crée pas !
* bouton Invert (inverser) : inverse le canal droit ce qui provoque un mix ressenti plus large à cause de la façon dont le cerveau interprète l'audio. Essayez-le et écoutez si ça sonne bien.
