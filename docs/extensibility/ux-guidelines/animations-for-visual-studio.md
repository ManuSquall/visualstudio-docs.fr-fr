---
title: Animations pour Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f113bf8d9a77e8569126a6f0c7d96f1fe4f0eea
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825241"
---
# <a name="animations-for-visual-studio"></a>Animations pour Visual Studio
## <a name="animation-fundamentals"></a>Principes de base de l’animation

### <a name="animation-best-practices-in-visual-studio"></a>Meilleures pratiques de l’animation dans Visual Studio
Suivez ces règles pour garantir des styles d’animation conviviale et cohérente au sein de l’IDE Visual Studio.

- **Soyez sélectif.** Limiter les animations à celles qui remplissent une fonction spécifique.

- **Minutage et vitesse sont importantes** pour vous assurer que l’impression de transitions naturelle et rapide :

  - Effectuer des transitions animées au sein d’une demi-seconde (500 millisecondes).

  - Les animations qui seraient produisent fréquemment doivent être suffisamment rapide pour qu’elles n’interrompront pas le flux de travail de l’utilisateur. Regardez l’animation dans une boucle et régler la durée jusqu'à ce qu’il semble correct.

  - Animations ne doit pas être tellement rapide ou souffrent qu’il est difficile à comprendre, mais pas tellement lent qu’elle effectue un impatiente la transition se terminer.

  - Utilisez le minutage de variable pour mettre en évidence d’importance. Par exemple, lors de la navigation dans une séquence d’éléments sur un diagramme de classes, permet d’accélérer le déplacement entre les transitions entre les éléments puis ralentir pour vous concentrer sur les éléments importants.

- **Utiliser l’accélération non linéaire progressive** d’un état à un autre, donner une idée de mouvement calme et naturelle.

- Dans la mesure du possible, **utiliser une animation subtile pointage** pour indiquer les éléments interactifs sous la souris.

- Si vous reposent largement sur les animations dans vos fonctionnalités, puis **fournissent un moyen de les mettre hors tension** localement (pour toutes les fonctionnalités) en tant qu’option dans le **Outils > Options** boîte de dialogue.

- **Qu’une seule animation doit se produire à la fois** et d’indiquer qu’un seul élément d’information. Plusieurs objets déplacement ou en essayant de transmettre plusieurs choses peuvent prêter à confusion.

- **Subtilité est importante.** Dans la plupart des cas, l’animation ne dispose à l’attention de l’utilisateur à la demande pour satisfaire à ses objectifs. Modifications subtiles dans la synchronisation, de séquencement et de comportement peuvent affecter considérablement la perception et peuvent faire la différence entre une animation efficace et inefficace.

- Lors de l’utilisation d’animation pour attirer l’attention sur quelque chose, **vous assurer qu’il est intéressant d’interrompre l’utilisateur**d’idée.

- **Lors de l’affichage de progression ou l’état** via animation :

  - Arrêter montrant le mouvement de progression lorsque le processus sous-jacent n’est pas avancer.

  - Distinguer les processus indéterminés des processus déterminées.

  - Vérifiez qu’une animation identifiables États d’exécution et l’échec.

  - Réduire l’utilisation des animations d’effet qui indiquent l’état et vous assurer qu’une valeur réelle en fournissant des informations supplémentaires d’utilisation réelle. En cas d’urgence et les changements d’état temporaires sont des exemples

#### <a name="animation-donts"></a>Avertissements d’animation :

- N’utilisez pas petits mouvements (déplacement dans un faible encombrement). Préférez fondus et changent au fil du déplacement d’objets.

- N’utilisez pas les animations qui se produisent sur une large zone d’écran. Quelle que soit la taille, ce style d’animation est gênant l’utilisateur.

- N’utilisez pas les animations non liés à l’objet de sur que l’utilisateur se concentre actuellement ou en interagissant avec.

- N’utilisez pas les animations qui nécessitent l’intervention de l’utilisateur de réinitialiser l’état, telles que de forcer l’utilisateur à répondre à une notification clignotante afin de la rendre arrêter clignotant. Interagir avec elles dans n’importe quel moyen devrait suffire faire disparaître les.

Pour plus d’informations sur les applications pour ces meilleures pratiques, consultez [modèles d’Animation](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métriques d’animation

- Le système doit visiblement réagir aux mouvements de l’utilisateur en moins de 10 millisecondes.

- Transitions animées ne devrait pas prendre plues de 500 millisecondes pour se terminer.

- Un pour compenser les transitions qui nécessitent des temps longs consiste à séparer en deux parties. Par exemple, la première partie d’une animation peut être le conteneur de contenu vide (jusqu'à 500 millisecondes), suivi de l’atténuation de contenu dans le conteneur (jusqu'à 500 millisecondes).

- Pour les temps de chargement peuvent être calculés, un indicateur de progression déterminante (indicateur de progression de terminé en %) est préférable.

- Pour les temps de chargement qui ne peut pas être calculés, un indicateur d’occupation comme un curseur ou une animation en rotation embedded (chargement ou indicateur de travail) est approprié.

### <a name="animation-as-communicator"></a>Animation en tant que communicator
Dans l’interface utilisateur de Visual Studio, l’animation fonctionne uniquement comme un outil de communication.  Il est utilisé pour communiquer une variété d’informations, telles que des modifications structurelles dans l’interface utilisateur (par exemple, lorsqu’un menu ouvre ou ferme). Animation peut aider à visualiser le comportement dépendant du temps des systèmes complexes, comme la visualisation de progression d’installation. Animations peuvent également être utilisées pour attirer l’attention des alertes et notifications.

 Animations de l’interface utilisateur fonctionnent généralement de quatre manières : visualiser, d’attirer l’attention, de simuler, et les heures de réponse/indicateurs de progression.

#### <a name="visualize"></a>Visualisation
Animation peut mettre l’accent sur la nature en trois dimensions d’objets et faciliter aux utilisateurs de visualiser leur structure spatiale. Pour ce faire, l’animation ont besoin pour mettre en place l’objet dans un cercle complet, lente de l’activer dans les deux sens, ou mettre l’objet plus proche et légèrement augmenter sa taille pour mettre en évidence une substitution ou le focus.

Bien que les objets en trois dimensions peuvent être déplacés avec le contrôle utilisateur, le concepteur doit déterminer à l’avance (par programmation ou manuellement) comment optimal animer un mouvement qui fournit une présentation optimale de l’objet. Cette programmées animation peut ensuite être activée par l’utilisateur en plaçant le curseur sur l’objet, tandis que les mouvements contrôlée par l’utilisateur nécessitent l’utilisateur à comprendre comment manipuler l’objet. Limiter le déplacement à un seul axe ou une orientation à la fois. mettre à l’échelle, faire pivoter, ou traduire, mais ne le faites pas plusieurs fois simultanément.

La catégorie de visualiser inclut les aspects de données, relations, état, structure, la séquence et temps.

##### <a name="data"></a>Données
Illustrer des informations complexes et de variable :

- Naviguer entre les visualisations informations tels que les graphiques

- Pas à pas détaillé dans une séquence, la visite guidée et la pagination

- Appel de détails, pointant vers et mise en évidence des informations spécifiques

- Détails de la superposition et des informations supplémentaires sur un élément ayant le focus

- Transformation d’une représentation structurelle ou d’organisation à l’autre

- Représentant les modifications au fil du temps à l’aide de curseurs de temps, les roues jog et shuttle et contrôles de transport (lecture, arrêt et pause)

##### <a name="relationships"></a>Relationships

- Illustrer comment les éléments sont liés entre eux ou les éléments associés à un élément donné

- Afficher les relations parent-enfant et hiérarchies ou les frères

- Un seul élément génère une autre

- Un seul élément réduit à un autre élément

- Un seul élément attaché à un autre

##### <a name="state"></a>État

- Mises à jour de contenu

- Sélection et le focus utilisateur

- Progression

- Errors

##### <a name="structure"></a>Structure

- Glissement de la structure sur un nœud

- Réorientation

- Réduire et agrandir, ou développer et réduire

##### <a name="sequence"></a>Séquence

- Séquence de diaporama

- Défiler les images

##### <a name="time"></a>Temps

- Afficher les modifications dans le temps, d’intervalle de temps et de capture vidéo

- Déplacer vers mettre, Annuler et rétablir

- Restaurer l’état de l’historique

#### <a name="attract-attention"></a>Attirer votre attention
Si l’objectif est pour attirer l’attention de l’utilisateur en un seul élément hors plusieurs ou pour avertir l’utilisateur pour les informations mises à jour, une animation peut convenir. Par exemple, page de démarrage de votre application peut utiliser un bouton de mise en route qui glisse en place une fois que la page se charge.

En règle générale, le dernier élément de déplacement sur l’écran attire l’attention des utilisateurs.  Dans une série d’éléments animés, attention de l’utilisateur suit le dernier objet mobile.

##### <a name="alert"></a>Alerte

- Avertir l’utilisateur, l’attention, afficher la progression

- Afficher les que quelque chose est effectuée correctement ou non ou afficher la progression ou les modifications de la progression

- Demander aux utilisateurs pendant une tâche, comme la recherche d’informations en ligne ou en savoir plus sur la tâche actuelle

##### <a name="notifications"></a>Notifications

- Alerter l’utilisateur sur une condition d’erreur

- Interrompre l’utilisateur pour voir s’il souhaite assister à quelque chose d’autre

- Doucement informer l’utilisateur qu’un processus est terminé ou modifié, comme lors d’un téléchargement est terminé.

#### <a name="simulate"></a>Simuler
Cette catégorie couvre physicality et dimensionnalité.

- Illustrer d'où proviennent les objets ou où ils accèdent à

- Développer et réduire ou ouvrir et fermer

- Panoramique, le défilement et la page active

- Empilement et l’ordre de plan

- Carrousel et accordion

- Retourner et faire pivoter l’interface utilisateur

#### <a name="response-and-progress-indicators"></a>Indicateurs de réponse et de progression
Indicateurs de progression ont quelques avantages importants :

- Les deux indicateurs de progression déterminée et indéterminé rassurer l’utilisateur que le système n’est pas tombé en panne et travaille sur le problème.

- Indicateurs déterminées donner à l’utilisateur que la progression d’une idée de l’avancement de l’action, ainsi que d’un sentiment de plus proches de la fin.

## <a name="BKMK_AnimationPatterns"></a> Modèles d’animation

### <a name="overview"></a>Présentation
Les animations dans Visual Studio sont conçues pour répondre à une fonction spécifique sans affecter négativement la productivité des utilisateurs. En règle générale, les animations dans Visual Studio doivent être :

- Petites et discrète

- Réalistes et naturelles

- Subtils et tamisée

- Rapide et efficace

- Assouplie, pressé ou ne disposant ne pas

Cette illustration montre les styles d’animation que nous recommandons pour Visual Studio. Aucune animation ou animations subtiles, comme l’apparition en fondu fondu ne sont les plus fréquemment utilisées. Il existe une application limitée d’animations de mouvement comme être accrus ou réduits, positions X et Y, modification et rotation.

![Recommandé de styles d’animation pour Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Styles d'animation recommandés pour Visual Studio

#### <a name="appear-and-disappear"></a>Apparaissent et disparaissent
Avec ce modèle, un élément bascule de visible hors de la vue et revenir sans une animation de transition.

![Apparaissent et disparaissent animation](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Apparaissent et disparaissent d’animation

##### <a name="correct-usage"></a>Utilisation correcte
Éléments d’interface utilisateur fraîches qui doivent instantanément apparaissent ou disparaissent afin que l’utilisateur n’est ni distraits ni momentanément. En outre, les animations lentes peuvent être perçues comme une opération de glissement de performances, ce qui n’a pas lieu avec le style s’affichent et disparaissent.

##### <a name="incorrect-usage"></a>Utilisation incorrecte
Cas dans lesquels l’utilisateur n’a aucune idée brusquement, interface utilisateur s’affiche que s’est-il passé, et ajout d’une animation serait utile avec la compréhension contextuelle.

##### <a name="animation-properties"></a>Propriétés de l’animation
Le délai est généralement zéro seconde.

##### <a name="examples"></a>Exemples
- Masquer les fenêtres Outil

- Interface utilisateur, telles qu’IntelliSense et aide sur les paramètres d’éditeur activés par le clavier

- Régions de code de développer et réduire

#### <a name="fade-in-and-fade-out"></a>Apparition en fondu et fondu
Avec ce modèle, un élément d’interface utilisateur passe de non visible (opacité de 0 %) visible (100 % d’opacité) et inversement.

![Animation apparition en fondu et fondu](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animation apparition en fondu et fondu

##### <a name="correct-usage"></a>Utilisation correcte
Ceci est le plus souvent recommandé animation de l’interface utilisateur. Il est un effet subtil qui ajoute un intérêt sans interrompre le flux. Dans certains cas, l’utilisateur ait conscience qu’il existe une animation, percevoir un smooth et circulant de système de l’interface utilisateur.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Opacité de départ : 0 % pour le fondu, 100 % pour le fondu

- Opacité de fin : 100 % pour le fondu, 0 % pour le fondu

- Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison

- Accélération de style : Sinus InOut

##### <a name="examples"></a>Exemples

- Masquer les fenêtres Outil

- Menu Ouvrir et fermer

- Transitions d’onglet en arrière-plan et de premier plan

#### <a name="color-blend-from-a-to-b"></a>Mélange de couleurs de A à B
Avec ce modèle, un élément d’interface utilisateur change de couleur A par couleur B.

![Animation mélange de couleurs](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animation de dégradé de couleur

##### <a name="correct-usage"></a>Utilisation correcte
En tant qu’une transition animée lorsqu’un élément d’interface utilisateur change de couleur à partir d’un contexte ou état vers un autre.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Couleur de début : L’interface utilisateur spécifique

- Couleur de fin : L’interface utilisateur spécifique

- Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison

- Accélération de style : Sinus InOut

##### <a name="examples"></a>Exemples

- Transitions d’état de fenêtre de document (active, la dernière actives et inactives)

- Transitions d’état de fenêtre d’outils (ayant le focus et inactif)

#### <a name="expand-and-contract"></a>Être accrus ou réduits
Avec ce modèle, un élément d’interface utilisateur se développe dans X, Y ou les deux sens.

![Être accrus ou réduits animation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Être accrus ou réduits d’animation

##### <a name="correct-usage"></a>Utilisation correcte
En tant qu’une transition animée lorsqu’un élément d’interface utilisateur modifie la taille d’un contexte à un autre.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Échelle x : % ou une dimension spécifique (en pixels)

- Mise à l’échelle Y : % ou une dimension spécifique (en pixels)

- Position de l’ancrage : en règle générale supérieur gauche (pour les langues de gauche à droite) ou supérieur droit (pour les langues de droite à gauche)

- Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison

##### <a name="examples"></a>Exemples

- Volet d’Explorateur de l’architecture développer / réduire

- Élément de Visual Studio 2017 Start Page développer / réduire

#### <a name="x-y-position-change"></a>X-Y positionner la modification
Avec ce modèle, un élément d’interface utilisateur change sa position X ou Y ou les deux.

![Animation de modification de position X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animation de modification de position X-Y

##### <a name="correct-usage"></a>Utilisation correcte
En tant qu’une transition animée lorsqu’un élément d’interface utilisateur change de position d’un contexte à un autre.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Position à partir de X et Y : L’interface utilisateur spécifique

- Fin X et Y position : L’interface utilisateur spécifique

- Chemin d’accès de mouvement : aucun

- Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison

- Accélération de style : Sinus InOut

##### <a name="example"></a>Exemples
Réorganisation de l’onglet

#### <a name="rotate"></a>Faire pivoter
Avec ce modèle, l’élément d’interface utilisateur fait pivoter.

![Animation de rotation de l’interface utilisateur élément](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animation de rotation de l’interface utilisateur élément

##### <a name="correct-usage"></a>Utilisation correcte
Uniquement pour l’indicateur de progression en rotation indéterminé.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Degré de rotation : 360

- Centre de rotation : central de l’objet

- Durée : continue

##### <a name="example"></a>Exemple
Indicateur de progression indéterminée (rotation)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Les actions de l’interface utilisateur shell courantes et les animations recommandées

#### <a name="tab-open"></a>Onglet ouvert
![Onglet animation ouvrir](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animation ouvrir l’onglet

- Style : apparaissent

- Durée : zéro seconde

#### <a name="tab-close"></a>Onglet fermer
![Onglet animation fermer](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animation fermer l’onglet

- Style : Changer de position X

- Durée : 200 millisecondes

#### <a name="tab-reorder"></a>Réorganisation de l’onglet
![Onglet animation réorganiser dans Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animation réorganiser l’onglet

- Style : Changer de position X

- Durée : 200 millisecondes

#### <a name="close-floating-document"></a>Fermer le document flottante
![Fermer flottante d’animation de document](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Animation de document flottante fermer

- Style : apparaissent

- Durée : 200 millisecondes

#### <a name="window-state-transition"></a>Transition d’état de fenêtre
![Animation de transition d’état fenêtre](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animation de transition d’état fenêtre

- Style : pour garantir une cohérence avec d’autres fenêtres, permettent du système d’exploitation actuel définir l’animation de fermeture du document.

- Durée : 200 millisecondes

#### <a name="menu-open"></a>Menu Ouvrir
![Animation ouvrir le menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animation ouvrir le menu

- Style : fondu

- Durée : 200 millisecondes

#### <a name="menu-close"></a>Menu fermer
![Animation fermer le menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animation fermer le menu

- Style : fondu

- Durée : 200 millisecondes

#### <a name="auto-hide-tool-window-reveal"></a>Divulgation de fenêtre outil de masquage automatique
![Animation de révéler la fenêtre outil à masquage automatique](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Animation de révéler la fenêtre outil à masquage automatique

- Style : apparaissent

- Durée : zéro seconde
