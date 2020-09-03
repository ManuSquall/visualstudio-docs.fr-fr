---
title: Animations
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825355"
---
# <a name="animations-for-visual-studio"></a>Animations pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Notions de base de l’animation

### <a name="animation-best-practices-in-visual-studio"></a>Meilleures pratiques pour l’animation dans Visual Studio
 Suivez ces règles pour garantir des styles d’animation cohérents et conviviaux entre l’IDE de Visual Studio.

- **Soyez sélectif.** Limitez les animations à celles qui répondent à des objectifs spécifiques.

- La **durée et la vitesse sont importantes** pour garantir une transition rapide et naturelle des transitions :

  - Effectuez des transitions animées en une demi-seconde (500 millisecondes).

  - Les animations qui se produisent fréquemment doivent être suffisamment rapides pour ne pas interrompre le flux de travail de l’utilisateur.

  - Les animations ne doivent pas être si rapides ou transférerez qu’elles sont difficiles à comprendre, mais elles ne sont pas si lentes qu’il y a un patient pour terminer la transition.

  - Utilisez la synchronisation des variables pour insister sur l’importance. Par exemple, lorsque vous parcourez une séquence d’éléments sur un diagramme de classes, vous pouvez accélérer les transitions entre les éléments, puis ralentir pour vous concentrer sur les éléments importants.

- **Utilisez une accélération non linéaire progressive** d’un État à un autre, en donnant un sens à un mouvement calme et naturel

- Lorsque cela est possible, **Utilisez une animation subtile au pointage** pour indiquer des éléments interactifs sous la souris.

- Si vous vous reposez fortement sur des animations dans vos fonctionnalités, vous pouvez les **Désactiver** localement (pour toutes vos fonctionnalités) en tant qu’option dans la boîte de dialogue **Outils > options** .

- Une **seule animation doit se produire à la fois** et transmettre un seul élément d’information.

- **La subtilité est importante.** Dans la plupart des cas, l’animation n’a pas besoin de demander l’attention de l’utilisateur pour servir son objectif. Des changements subtils dans le minutage, le séquencement et le comportement peuvent avoir un impact significatif sur la perception et peuvent faire la différence entre une animation efficace et inefficace.

- Lorsque vous utilisez l’animation pour attirer l’attention sur quelque valeur, **Assurez-vous qu’il est utile d’interrompre la formation de l’utilisateur**.

- **Lors de l’indication de la progression ou de l’État** via l’animation :

  - Arrêter l’indication du déplacement de la progression lorsque le processus sous-jacent n’est pas en cours d’avancement.

  - Distinguez les processus indéterminés des processus de déterminaison.

  - Assurez-vous qu’une animation a des États d’achèvement et d’échec identifiables.

  - Réduisez l’utilisation des animations d’effet qui affichent l’État et assurez-vous qu’elles ont une valeur réelle en fournissant des informations supplémentaires sur l’utilisation réelle. Exemples : modifications d’État transitoires et situations d’urgence

#### <a name="do-not"></a>Ne pas :

- Utilisez de petits mouvements (déplacement dans un faible encombrement), en préférant les fondues et les modifications sur les objets mobiles.

- Utilisez les animations qui se produisent sur une vaste zone de l’écran. Quelle que soit la taille, ce style d’animation gêne l’utilisateur.

- Utilisez des animations qui ne sont pas liées à l’objet sur lequel l’utilisateur est actuellement axé ou qui interagit.

- Utilisez des animations qui requièrent une interaction de l’utilisateur pour réinitialiser l’État, par exemple obliger l’utilisateur à répondre à une notification clignotante afin qu’il cesse de clignoter. L’interaction avec eux doit être suffisante pour les faire disparaître.

  Pour plus d’informations sur les applications pour ces meilleures pratiques, consultez [modèles d’animation](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Métriques d’animation

- Le système doit réagir de façon visible aux gestes de l’utilisateur en moins de 10 millisecondes.

- Les transitions animées ne doivent pas durer plus de 500 millisecondes.

- Pour compenser les transitions qui nécessitent plus de temps, il est possible de la séparer en deux parties ; par exemple, la première partie d’une animation peut être le conteneur de contenu vide (jusqu’à 500 millisecondes) suivi du contenu dans le conteneur (jusqu’à 500 millisecondes).

- Pour les temps de chargement qui peuvent être calculés, un indicateur de progression déterminant (indicateur de progression en pourcentage) est préféré.

- Pour les temps de chargement qui ne peuvent pas être calculés, un indicateur occupé, tel qu’un curseur ou une animation à rotation intégrée (indicateur de chargement ou de travail) est approprié.

### <a name="animation-as-communicator"></a>Animation comme Communicator
 Dans l’interface utilisateur de Visual Studio, l’animation fonctionne uniquement comme un outil de communication.  Il sert à communiquer diverses informations, telles que les modifications structurelles dans l’interface utilisateur. par exemple, lorsqu’un menu s’ouvre ou se ferme. L’animation peut vous aider à visualiser le comportement dépendant du temps des systèmes complexes, tels que la visualisation de la progression de l’installation ou à être utilisé pour attirer l’attention sur les alertes et les notifications.

 Les animations d’interface utilisateur fonctionnent généralement de quatre façons : visualiser, attirer l’attention, simuler et indiquer les temps de réponse/la progression.

#### <a name="visualize"></a>Visualiser
 L’animation peut mettre en évidence la nature à trois dimensions des objets et permettre aux utilisateurs de visualiser plus facilement leur structure spatiale. Pour ce faire, il se peut que l’animation doive faire pivoter l’objet dans un cercle entier, le faire tourner lentement, ou rapprocher l’objet et augmenter légèrement sa taille pour insister sur la substitution ou le focus.

 Même si les objets tridimensionnels peuvent être déplacés avec le contrôle utilisateur, le concepteur doit déterminer à l’avance (par programmation ou manuellement) comment animer au mieux un mouvement qui fournit une compréhension optimale de l’objet. Cette animation programmée peut ensuite être activée par l’utilisateur en plaçant le curseur sur l’objet, tandis que les mouvements contrôlés par l’utilisateur requièrent que l’utilisateur sache comment manipuler l’objet. Limitez le mouvement à un axe unique ou à une orientation à la fois ; mettre à l’échelle, faire pivoter ou traduire, mais ne pas en faire plusieurs simultanément.

 La catégorie visualiser comprend les aspects des données, des relations, de l’État, de la structure, de la séquence et de l’heure.

##### <a name="data"></a>Données
 Illustrer des informations complexes et variables :

- Déplacement à travers des visualisations d’informations telles que des graphiques et des graphiques

- Exécution pas à pas d’une séquence, visite guidée et pagination

- Appeler des détails, pointer et mettre en évidence des informations spécifiques

- Superposer des détails et des informations supplémentaires sur un élément ayant le focus

- Transformation d’une représentation structurelle ou organisationnelle en une autre

- Représentation des modifications au fil du temps à l’aide de curseurs temporels, de roulettes Jog-and-Shuttle et de contrôles de transport (lecture, arrêt et pause).

##### <a name="relationships"></a>Relations

- Illustrer comment les éléments sont liés l’un à l’autre ou quels éléments sont associés à un élément donné.

- Afficher les hiérarchies et les relations parent-enfant ou frères

- Un élément engendre une autre

- Un élément réduit à un autre élément

- Un élément est attaché à un autre

##### <a name="state"></a>State

- Mises à jour de contenu.

- Focus et sélection de l’utilisateur

- Avancement

- Erreurs

##### <a name="structure"></a>Structure

- Faire pivoter la structure sur un nœud

- Réorientant

- Réduire et agrandir, ou développer et réduire

##### <a name="sequence"></a>Séquence

- Séquence de diaporama

- Retournement des images

##### <a name="time"></a>Temps

- Afficher les modifications au fil du temps, de l’heure et de la capture vidéo

- Déplacer vers la corbeille, annuler et rétablir

- Restaurer l’état d’historique

#### <a name="attract-attention"></a>Attirer l’attention
 Si l’objectif est de attirer l’attention de l’utilisateur sur un seul élément à partir de plusieurs ou d’alerter l’utilisateur à des informations mises à jour, une animation peut être appropriée. Par exemple, la page de démarrage de vos applications peut utiliser un bouton Prise en main qui est placé après le chargement de la page.

 En règle générale, le dernier élément en déplacement à l’écran attire l’attention de l’utilisateur.  Dans une série d’éléments animés, l’attention de l’utilisateur suivra le dernier objet en déplacement.

##### <a name="alert"></a>Alerte

- Alertez l’utilisateur, soyez attentif, affichez la progression

- Indique que l’opération est effectuée correctement ou de manière incorrecte, ou affiche les modifications de progression ou de progression

- Invitez les utilisateurs pendant une tâche, par exemple pour rechercher plus d’informations en ligne ou en savoir plus sur la tâche en cours

##### <a name="notifications"></a>Notifications

- Alerter l’utilisateur à propos d’une condition d’erreur

- Interrompre l’utilisateur pour voir s’il souhaite participer à autre chose

- Informez doucement l’utilisateur qu’un processus est terminé ou modifié, par exemple lorsqu’un téléchargement est terminé.

#### <a name="simulate"></a>Simuler
 Cette catégorie couvre la physique et la dimensionnalité.

- Illustrer l’emplacement d’origine ou l’emplacement d’accès aux objets

- Développer et réduire ou ouvrir et fermer

- Panoramiques, défilement et tours de page

- Empilage et ordre de plan

- Carrousel et accordéon

- Basculement et rotation de l’interface utilisateur

#### <a name="response-and-progress-indicators"></a>Indicateurs de réponse et de progression
 Les indicateurs de progression présentent quelques avantages notables :

- Les indicateurs de progression déterminés et indéterminés confirment à l’utilisateur que le système ne s’est pas bloqué et qu’il travaille sur le problème.

- Les indicateurs de fin donnent à l’utilisateur un sens de la progression de l’action, ainsi qu’une sensation de plus près de la fin.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Modèles d’animation

### <a name="overview"></a>Vue d’ensemble
 Les animations dans Visual Studio sont destinées à servir une fonction spécifique et n’empêchent pas la productivité des utilisateurs. Les caractéristiques d’animation générales à respecter sont les suivantes :

- Petit et discret

- Naturel et réaliste

- Discret et subdued

- Rapide et efficace

- Souple, non constaté

  L’illustration suivante montre les styles d’animation recommandés pour une utilisation dans Visual Studio. Il n’y a pas d’animation et d’animations subtiles, telles que les fondus/disparitions, qui sont les plus fréquemment utilisées. Il existe une application limitée d’animations de mouvement, telles que le développement et le contrat, le changement de position X et Y et la rotation.

  ![Styles d'animation recommandés pour Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Styles d'animation recommandés pour Visual Studio**

#### <a name="appear-and-disappear"></a>Apparaissent et disparaissent
 Avec ce modèle, un élément bascule de visible à hors vue et de retour sans animation de transition :

 ![S’affiche&#47;disparition de l’animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

##### <a name="correct-usage"></a>Utilisation correcte
 Nouveaux éléments d’interface utilisateur qui doivent instantanément apparaître ou disparaître afin que l’utilisateur ne soit pas gêné ni obstrué. En outre, les animations à déplacement lent peuvent être perçues comme un glissement des performances, ce qui ne se produit pas avec le style d’apparition et de disparition.

##### <a name="incorrect-usage"></a>Utilisation incorrecte
 Cas dans lesquels l’interface utilisateur apparaît si brusquement, l’utilisateur n’a aucune idée de ce qui s’est passé, et l’ajout d’une animation peut faciliter la compréhension contextuelle.

##### <a name="animation-properties"></a>Propriétés de l’animation
 Le délai est généralement de zéro seconde.

##### <a name="examples"></a>Exemples

- Masquer automatiquement les fenêtres outil

- Interface utilisateur de l’éditeur activée par le clavier, telle que IntelliSense et l’aide sur les paramètres

- Développer et réduire les zones de code

#### <a name="fade-in-and-fade-out"></a>Fondu-entrée et disparition en fondu
 Avec ce modèle, un élément d’interface utilisateur passe de l’état non visible (opacité de 0%) à l’état visible (opacité de 100%), ou vice versa :

 ![&#45;fondu dans&#47;&#45;fondu de l’animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>Utilisation correcte
 Il s’agit de l’animation d’interface utilisateur la plus couramment recommandée. Il s’agit d’un effet subtil qui ajoute un intérêt sans interrompre le processus. Dans certains cas, l’utilisateur peut même ne pas se rendre compte qu’il existe une animation et perçoit simplement un système d’interface utilisateur fluide fluide.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Opacité de départ : 0% pour le fondu, 100% pour le fondu

- Opacité de fin : 100% pour fondu-entrée, 0% pour disparition en fondu

- Durée : 200 millisecondes en mode autonome, 100 millisecondes lorsqu’il est utilisé dans le cadre d’une séquence d’animation combinée

- Style d’accélération : sinus InOut

##### <a name="examples"></a>Exemples

- Masquer automatiquement les fenêtres outil

- Menu ouvrir et fermer

- Transitions d’onglets d’arrière-plan et de premier plan

#### <a name="color-blend-from-a-to-b"></a>Fusion des couleurs de A à B
 Avec ce modèle, un élément d’interface utilisateur passe de la couleur A à la couleur B :

 ![Animation Mélange de couleurs dans Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

##### <a name="correct-usage"></a>Utilisation correcte
 En tant que transition animée lorsqu’un élément d’interface utilisateur change de couleur d’un contexte ou d’un État à un autre.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Couleur de début : spécifique à l’interface utilisateur

- Couleur de fin : spécifique à l’interface utilisateur

- Durée : 200 millisecondes en mode autonome, 100 millisecondes lorsqu’il est utilisé dans le cadre d’une séquence d’animation combinée

- Style d’accélération : sinus InOut

##### <a name="examples"></a>Exemples

- Transitions d’état de la fenêtre de document (active, dernière activité et inactive)

- Transitions d’état de la fenêtre outil (Focus et inactif)

#### <a name="expand-and-contract"></a>Développer et contracter
 Avec ce modèle, un élément d’interface utilisateur se développe dans les directions X, Y ou les deux :

 ![Développer&#47;animation de contrat dans Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>Utilisation correcte
 En tant que transition animée lorsqu’un élément d’interface utilisateur change de taille d’un contexte à un autre.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Échelle X :% ou dimension spécifique (en pixels)

- Échelle Y :% ou une dimension spécifique (en pixels)

- Position d’ancrage : généralement en haut à gauche (pour les langues de gauche à droite) ou en haut à droite (pour les langues de droite à gauche)

- Durée : 200 millisecondes en mode autonome, 100 millisecondes lorsqu’il est utilisé dans le cadre d’une séquence d’animation combinée

##### <a name="examples"></a>Exemples

- Développement et réduction du volet Explorateur d’architecture

- Développer et réduire l’élément de la page de démarrage

#### <a name="x-y-position-change"></a>Modification de la position X-Y
 Avec ce modèle, un élément d’interface modifie sa position X ou Y, ou les deux :

 ![Animation de modification de la position X&#47;Y dans Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

##### <a name="correct-usage"></a>Utilisation correcte
 En tant que transition animée lorsqu’un élément de l’interface utilisateur change de position d’un contexte à un autre.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Position de départ X et Y : spécifique à l’interface utilisateur

- Position de fin X et Y : spécifique à l’interface utilisateur

- Trajectoire : aucune

- Durée : 200 millisecondes en mode autonome, 100 millisecondes lorsqu’il est utilisé dans le cadre d’une séquence d’animation combinée

- Style d’accélération : sinus InOut

##### <a name="example"></a>Exemple
 Réorganisation des tabulations

#### <a name="rotate"></a>Faire pivoter
 Avec ce modèle, l’élément d’interface utilisateur pivote :

 ![Animation Faire pivoter dans Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

##### <a name="correct-usage"></a>Utilisation correcte
 Uniquement pour l’indicateur de progression de rotation indéterminé.

##### <a name="animation-properties"></a>Propriétés de l’animation

- Degré de rotation : 360

- Centre de rotation : milieu de l’objet

- Durée : continue

##### <a name="example"></a>Exemple
 Indicateur de progression indéterminé (rotation)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Actions courantes de l’interface utilisateur du shell et animations recommandées

#### <a name="tab-open"></a>Onglet ouvert

- Style : apparaît

- Durée : zéro seconde

  ![Animation Ouvrir l'onglet dans Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>Fermer la tabulation

- Style : modification de la position X

- Durée : 200 millisecondes

  ![Animation Fermer l'onglet dans Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>Réorganisation de l’onglet

- Style : modification de la position X

- Durée : 200 millisecondes

  ![Animation Réorganiser l'onglet dans Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>Fermer le document flottant

- Style : apparaît

- Durée : 200 millisecondes

  ![Fermer l'animation de document flottante dans Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Transition de l’état de la fenêtre

- Style : pour être cohérent avec d’autres fenêtres, laissez le système d’exploitation actuel définir l’animation de fermeture du document.

- Durée : 200 millisecondes

  ![Animations de transition d'état de fenêtre dans Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>Menu ouvert

- Style : fondu

- Durée : 200 millisecondes

  ![Animation Ouvrir le menu dans Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>Fermer le menu

- Style : disparition en fondu

- Durée : 200 millisecondes

  ![Animation Fermer le menu dans Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Masquer automatiquement la fenêtre outil révéler

- Style : apparaît

- Durée : zéro seconde

  ![Animation&#45;masquer la fenêtre outil dans Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
