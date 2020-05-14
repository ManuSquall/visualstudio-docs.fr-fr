---
title: Animations pour Visual Studio (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698605"
---
# <a name="animations-for-visual-studio"></a>Animations pour Visual Studio
## <a name="animation-fundamentals"></a>Principes fondamentaux de l’animation

### <a name="animation-best-practices-in-visual-studio"></a>Les meilleures pratiques d’animation en studio visuel
Suivez ces règles pour assurer des styles d’animation cohérents et conviviaux à travers l’IDE Visual Studio.

- **Soyez sélectif.** Limitez les animations à celles qui servent des fins spécifiques.

- **Le moment et la vitesse sont importants** pour s’assurer que les transitions se sentent rapides et naturelles :

  - Effectuer des transitions animées en une demi-seconde (500 millisecondes).

  - Les animations qui se produiraient fréquemment doivent être assez rapides pour ne pas interrompre le flux de travail de l’utilisateur. Regardez l’animation en boucle et ajustez le timing jusqu’à ce qu’il se sente bien.

  - Les animations ne devraient pas être si rapides ou choquantes qu’il est difficile à comprendre, mais pas si lent qu’il rend impatient pour la transition à la fin.

  - Utilisez le timing variable pour souligner l’importance. Par exemple, lorsque vous naviguez à travers une séquence d’éléments sur un diagramme de classe, accélérez les transitions entre les éléments, puis ralentissez pour se concentrer sur des éléments importants.

- **Utilisez un assouplissement progressif non linéaire** d’un état à l’autre, donnant un sentiment de calme et de mouvement naturel.

- Dans la mesure du possible, **utilisez une animation subtile sur le plan stationnaire** pour indiquer des éléments interactifs sous la souris.

- Si vous comptez beaucoup sur des animations dans vos fonctionnalités, puis **fournir un moyen de les désactiver** localement (pour toutes vos fonctionnalités) comme une option dans le dialogue Tools > **Options.**

- **Une seule animation doit se produire à la fois** et transmettre un seul élément d’information. Plus d’un objet se déplaçant ou essayant de transmettre plusieurs choses peut être déroutant.

- **La subtilité est importante.** Dans la plupart des cas, l’animation n’a pas besoin d’exiger l’attention des utilisateurs pour servir son but. Des changements subtils dans le timing, le séquençage et le comportement pourraient avoir un impact significatif sur la perception, et peuvent faire la différence entre une animation efficace et inefficace.

- Lorsque vous utilisez l’animation pour attirer l’attention sur quelque chose, **assurez-vous qu’il vaut la peine d’interrompre le**train de pensée de l’utilisateur.

- **Lors de l’affichage des progrès ou du statut** par l’animation:

  - Cessez de montrer le mouvement de progression lorsque le processus sous-jacent n’avance pas.

  - Distinguer les processus pour une période indéterminée des processus déterminés.

  - Assurez-vous qu’une animation a des états d’achèvement et d’échec identifiables.

  - Minimisez l’utilisation d’animations d’effets qui affichent l’état et assurez-vous qu’elles ont une valeur réelle en fournissant des informations supplémentaires d’utilisation réelle. Les exemples incluent les changements d’état transitoires et les urgences

#### <a name="animation-donts"></a>Animation don’ts:

- N’utilisez pas de petits mouvements (mouvement dans une petite empreinte). Préférez les fondus et les changements aux objets en mouvement.

- N’utilisez pas d’animations qui se déroulent sur une grande surface d’écran immobilier. Quelle que soit sa taille, ce style d’animation est distrayant pour l’utilisateur.

- N’utilisez pas d’animations sans rapport avec l’objet sur qui l’utilisateur est actuellement focalisé ou en interaction avec.

- N’utilisez pas d’animations qui nécessitent une interaction utilisateur pour réinitialiser l’état, comme forcer l’utilisateur à répondre à une notification clignotante afin de le faire cesser de clignoter. Interagir avec eux de quelque façon que ce soit devrait suffire à les rejeter.

Pour plus d’informations sur les applications pour ces meilleures pratiques, voir [Les modèles d’animation](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Mesures d’animation

- Le système doit réagir visiblement aux gestes de l’utilisateur en moins de 10 millisecondes.

- Les transitions animées ne devraient pas prendre plus de 500 millisecondes pour terminer.

- Une façon de compenser les transitions qui nécessitent des temps plus longs est de le séparer en deux parties. Par exemple, la première partie d’une animation pourrait être le contenant de contenu vide (jusqu’à 500 millisecondes), suivi de la décoloration du contenu dans le conteneur (jusqu’à 500 millisecondes).

- Pour les temps de chargement qui peuvent être calculés, un indicateur de progression déterminant (indicateur de progression fait pour cent) est préférable.

- Pour les temps de chargement qui ne peuvent pas être calculés, un indicateur occupé comme un curseur ou une animation de filature intégrée (indicateur de chargement ou de travail) est approprié.

### <a name="animation-as-communicator"></a>Animation en tant que communicateur
Dans Visual Studio UI, l’animation ne fonctionne qu’en tant qu’outil de communication.  Il est utilisé pour communiquer une variété d’informations, comme les changements structurels dans l’interface utilisateur (par exemple, quand un menu s’ouvre ou ferme). L’animation peut aider à visualiser le comportement dépendant du temps des systèmes complexes, comme la visualisation du progrès de l’installation. Les animations peuvent également être utilisées pour attirer l’attention avec des alertes et des notifications.

 Les animations d’interface utilisateur fonctionnent généralement de quatre façons : visualiser, attirer l’attention, simuler et les temps de réponse/indicateurs de progression.

#### <a name="visualize"></a>Visualisation
L’animation peut mettre l’accent sur la nature tridimensionnelle des objets et faciliter la visualisation de leur structure spatiale par les utilisateurs. Pour ce faire, l’animation peut avoir besoin de faire tourner l’objet en cercle complet, lentement le tourner d’avant en arrière, ou de rapprocher l’objet et légèrement augmenter sa taille pour mettre l’accent sur le renversement ou la mise au point.

Bien que les objets tridimensionnels puissent être déplacés avec le contrôle de l’utilisateur, le concepteur doit déterminer à l’avance (programmatiquement ou manuellement) comment mieux animer un mouvement qui fournit une compréhension optimale de l’objet. Cette animation programmée peut alors être activée par l’utilisateur en plaçant le curseur sur l’objet, tandis que les mouvements contrôlés par l’utilisateur exigent que l’utilisateur comprenne comment manipuler l’objet. Limiter le mouvement à un seul axe ou orientation à la fois; échelle, rotation ou traduire, mais ne faites pas plus d’un simultanément.

La catégorie Visualize comprend les aspects des données, des relations, de l’état, de la structure, de la séquence et du temps.

##### <a name="data"></a>Données
Illustrer les informations complexes et variables :

- Passer à travers des visualisations d’information comme des graphiques et des graphiques

- Passer à travers une séquence, visite guidée et paaging

- Appeler les détails, pointer et mettre en évidence des informations spécifiques

- Superposer les détails et les informations supplémentaires en plus d’un élément ciblé

- Morphing d’une représentation structurelle ou organisationnelle à une autre

- Représenter les changements au fil du temps à l’aide de curseurs de temps, de roues de jogging et de navette et de commandes de transport (jeu, arrêt et pause)

##### <a name="relationships"></a>Relations

- Illustrer comment les éléments se rapportent les uns aux autres ou quels éléments se rapportent à un élément donné

- Afficher les hiérarchies et les relations parents-enfants ou frères et sœurs

- Un élément engendre un autre

- Un élément minimise à un autre élément

- Un élément attaché à un autre

##### <a name="state"></a>State

- Mises à jour du contenu

- Attention et sélection de l’utilisateur

- Progress

- Erreurs

##### <a name="structure"></a>Structure

- Pivoter la structure sur un nœud

- Réorientation

- Minimiser et maximiser, ou d’élargir et de s’effondrer

##### <a name="sequence"></a>Séquence

- Séquence diaporama

- Feuilleter les images

##### <a name="time"></a>Temps

- Afficher le changement au fil du temps, le time lapse et le screencast

- Déplacez-vous à la poubelle, annuler et refaire

- Restaurer l’état historique

#### <a name="attract-attention"></a>Attirer l’attention
Si le but est d’attirer l’attention de l’utilisateur sur un seul élément de plusieurs ou d’alerter l’utilisateur à l’information mise à jour, alors une animation peut être appropriée. Par exemple, votre page de début d’application peut utiliser un bouton Getting Started qui glisse en place après la charge de la page.

En règle générale, le dernier élément mobile sur l’écran attire l’attention de l’utilisateur.  Dans une série d’éléments animés, l’attention de l’utilisateur suivra le dernier objet en mouvement.

##### <a name="alert"></a>Alerte

- Alerter l’utilisateur, attirer l’attention, montrer les progrès

- Montrez que quelque chose est fait correctement ou incorrectement ou montrez des changements de progrès ou de progrès

- Inciter les utilisateurs au cours d’une tâche, comme trouver plus d’informations en ligne ou en apprendre davantage sur la tâche actuelle

##### <a name="notifications"></a>Notifications

- Alerter l’utilisateur au sujet d’une condition d’erreur

- Interrompre l’utilisateur pour voir s’il aimerait s’occuper d’autre chose

- Informez doucement l’utilisateur qu’un processus est terminé ou modifié, comme lorsqu’un téléchargement est terminé.

#### <a name="simulate"></a>Simuler
Cette catégorie couvre la physicalité et la dimensionnalité.

- Illustrer d’où viennent les objets ou où ils vont

- Étendre et s’effondrer ou ouvrir et fermer

- Panoramique, défilement et tour de page

- Empilage et z-commande

- Carrousel et accordéon

- Retourner et faire tourner l’interface utilisateur

#### <a name="response-and-progress-indicators"></a>Indicateurs de réponse et de progrès
Les indicateurs de progression présentent quelques avantages notables :

- Les indicateurs de progression pour une période déterminée et indéterminée rassurent l’utilisateur que le système ne s’est pas écrasé et travaille sur le problème.

- Les indicateurs déterminés donnent à l’utilisateur une idée de la distance parcourue par l’action, ainsi que le sentiment de se rapprocher de l’arrivée.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Modèles d’animation

### <a name="overview"></a>Vue d'ensemble
Les animations dans Visual Studio sont destinées à servir une fonction spécifique sans entraver la productivité de l’utilisateur. En général, les animations dans Visual Studio devraient être :

- Petit et discret

- Naturel et réaliste

- Subtile et tamisée

- Rapide et efficace

- Détendu, pas pressé

Cette illustration montre les styles d’animation que nous recommandons pour Visual Studio. Aucune animation ou animations subtiles comme fade in/fade out ne sont les plus fréquemment utilisées. Il y a application limitée des animations de mouvement comme l’expansion et le contrat, le changement de position X et Y, et la rotation.

![Styles d'animation recommandés pour Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Styles d'animation recommandés pour Visual Studio

#### <a name="appear-and-disappear"></a>Apparaître et disparaître
Avec ce modèle, un élément passe du visible au hors-vue et au dos sans animation de transition.

![Apparaître et disparaître l’animation](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Apparaître et disparaître l’animation

##### <a name="correct-usage"></a>Utilisation correcte
Éléments d’interface utilisateur frais qui doivent apparaître instantanément ou disparaître de sorte que l’utilisateur n’est ni distrait ni obstrué. En outre, les animations lentes peuvent être perçues comme une traînée de performance, qui ne se produira pas avec le style d’apparence et de disparition.

##### <a name="incorrect-usage"></a>Utilisation incorrecte
Les cas dans lesquels l’interface utilisateur apparaît si brusquement l’utilisateur n’a aucune idée de ce qui s’est passé, et l’ajout d’une animation aiderait à la compréhension contextuelle.

##### <a name="animation-properties"></a>Propriétés d’animation
Le délai est généralement de zéro seconde.

##### <a name="examples"></a>Exemples
- Fenêtres d’outils auto-cacher

- Interface utilisateur d’éditeur activée par clavier, comme IntelliSense et Paramètre Help

- Régions de code d’expansion et d’effondrement

#### <a name="fade-in-and-fade-out"></a>Fade-in et fade-out
Avec ce modèle, un élément d’interface utilisateur passe de non visible (0% opacité) à visible (100% opacité) ou vice versa.

![Animation fade-in et fade-out](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animation fade-in et fade-out

##### <a name="correct-usage"></a>Utilisation correcte
Il s’agit de l’animation l’interface utilisateur la plus souvent recommandée. C’est un effet subtil qui ajoute de l’intérêt sans interrompre le flux. Dans certains cas, l’utilisateur pourrait même ne pas se rendre compte qu’il ya une animation, percevant un système d’interface utilisateur lisse et fluide.

##### <a name="animation-properties"></a>Propriétés d’animation

- Opacité de départ: 0% pour fade-in, 100% pour fade-out

- Fin de l’opacité: 100% pour fade-in, 0% pour fade-out

- Durée: 200 millisecondes autonomes, 100 millisecondes lorsqu’ils sont utilisés dans le cadre d’une séquence d’animation combinée

- Style d’assouplissement: Sine InOut

##### <a name="examples"></a>Exemples

- Fenêtres d’outils auto-cacher

- Menu ouvert et fermé

- Transitions de fond et d’onglet de premier plan

#### <a name="color-blend-from-a-to-b"></a>Mélange de couleur de A à B
Avec ce modèle, un élément d’interface utilisateur passe de la couleur A à la couleur B.

![Animation de mélange de couleur](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animation de mélange de couleur

##### <a name="correct-usage"></a>Utilisation correcte
En tant que transition animée lorsqu’un élément d’interface utilisateur change de couleur d’un contexte ou d’un état à un autre.

##### <a name="animation-properties"></a>Propriétés d’animation

- Couleur de départ : interface utilisateur spécifique

- Fin de la couleur: UI-spécifique

- Durée: 200 millisecondes autonomes, 100 millisecondes lorsqu’ils sont utilisés dans le cadre d’une séquence d’animation combinée

- Style d’assouplissement: Sine InOut

##### <a name="examples"></a>Exemples

- Transitions d’état de fenêtre de document (active, dernière active et inactive)

- Transitions d’état de fenêtre d’outil (ciblées et floues)

#### <a name="expand-and-contract"></a>Élargir et contracter
Avec ce modèle, un élément d’interface utilisateur se développe dans les directions X, Y ou les deux.

![Développer et contracter l’animation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Développer et contracter l’animation

##### <a name="correct-usage"></a>Utilisation correcte
En tant que transition animée lorsqu’un élément d’interface utilisateur change de taille d’un contexte à l’autre.

##### <a name="animation-properties"></a>Propriétés d’animation

- Échelle X : % ou dimension spécifique (en pixels)

- Échelle Y : % ou dimension spécifique (en pixels)

- Position d’ancrage : généralement en haut à gauche (pour les langues de gauche à droite) ou en haut à droite (pour les langues de droite à gauche)

- Durée: 200 millisecondes autonomes, 100 millisecondes lorsqu’ils sont utilisés dans le cadre d’une séquence d’animation combinée

##### <a name="examples"></a>Exemples

- Le panneau Architecture Explorer s’élargit et s’effondre

- Visual Studio 2017 Démarrer l’élément De la page d’expansion et de l’effondrement

#### <a name="x-y-position-change"></a>Changement de position X-Y
Avec ce modèle, un élément d’interface utilisateur modifie sa position X ou Y ou les deux.

![Animation de changement de position X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animation de changement de position X-Y

##### <a name="correct-usage"></a>Utilisation correcte
En tant que transition animée lorsqu’un élément d’interface utilisateur change de position d’un contexte à l’autre.

##### <a name="animation-properties"></a>Propriétés d’animation

- Démarrage de la position X et Y : spécifique à l’interface utilisateur

- Mettre fin à la position X et Y : spécifique à l’interface utilisateur

- Chemin de mouvement : aucun

- Durée: 200 millisecondes autonomes, 100 millisecondes lorsqu’ils sont utilisés dans le cadre d’une séquence d’animation combinée

- Style d’assouplissement: Sine InOut

##### <a name="example"></a>Exemple
Réorganiser l’onglet

#### <a name="rotate"></a>Faire pivoter
Avec ce modèle, l’élément d’interface utilisateur tourne.

![Animation de rotation des éléments de l’interface utilisateur](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animation de rotation des éléments de l’interface utilisateur

##### <a name="correct-usage"></a>Utilisation correcte
Seulement pour l’indicateur de progression de rotation indéterminée.

##### <a name="animation-properties"></a>Propriétés d’animation

- Degré de rotation: 360

- Centre de rotation : milieu de l’objet

- Durée: continue

##### <a name="example"></a>Exemple
Indicateur de progrès indéterminé (spinning)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Actions courantes d’interface utilisateur de coquille et animations recommandées

#### <a name="tab-open"></a>Onglet ouvert
![Animation ouverte d’onglet](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animation ouverte d’onglet

- Style: apparaître

- Durée: zéro secondes

#### <a name="tab-close"></a>Fermeture de l’onglet
![Tab animation étroite](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Tab animation étroite

- Style: X changement de position

- Durée: 200 millisecondes

#### <a name="tab-reorder"></a>Réorganiser l’onglet
![Animation Réorganiser l'onglet dans Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animation de réorganisation de l’onglet

- Style: X changement de position

- Durée: 200 millisecondes

#### <a name="close-floating-document"></a>Document flottant étroit
![Fermer l’animation flottante de document](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Fermer l’animation flottante de document

- Style: apparaître

- Durée: 200 millisecondes

#### <a name="window-state-transition"></a>Transition de l’état de fenêtre
![Animation de transition d’état de fenêtre](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animation de transition d’état de fenêtre

- Style : pour être cohérent avec d’autres fenêtres, laissez le système d’exploitation actuel définir l’animation proche du document.

- Durée: 200 millisecondes

#### <a name="menu-open"></a>Menu ouvert
![Animation ouverte au menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animation ouverte au menu

- Style: fade-in

- Durée: 200 millisecondes

#### <a name="menu-close"></a>Menu à proximité
![Menu animation proche](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Menu animation proche

- Style: fade-out

- Durée: 200 millisecondes

#### <a name="auto-hide-tool-window-reveal"></a>Fenêtre d’outil de cache automatique révèlent
![La fenêtre d’outil de cache automatique révèle l’animation](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />La fenêtre d’outil de cache automatique révèle l’animation

- Style: apparaître

- Durée: zéro secondes
