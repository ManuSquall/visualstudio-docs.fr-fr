---
title: Animations pour Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ba2f13ff484f73a7455089ccf2689037eabebdc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824397"
---
# <a name="animations-for-visual-studio"></a>Animations pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Principes de base de l’animation  
  
### <a name="animation-best-practices-in-visual-studio"></a>Meilleures pratiques de l’animation dans Visual Studio  
 Suivez ces règles pour garantir des styles d’animation conviviale et cohérente au sein de l’IDE de Visual Studio.  
  
-   **Soyez sélectif.** Limiter les animations à celles qui remplissent une fonction spécifique.  
  
-   **Minutage et vitesse sont importantes** pour vous assurer que l’impression de transitions naturelle et rapide :  
  
    -   Effectuer des transitions animées au sein d’une demi-seconde (500 millisecondes).  
  
    -   Les animations qui seraient produisent fréquemment doivent être suffisamment rapide pour qu’elles n’interrompront pas le flux de travail de l’utilisateur.  
  
    -   Animations ne doivent pas être tellement rapide ou souffrent qu’il est difficile à comprendre, mais pas tellement lent qu’elle effectue un impatiente la transition se terminer.  
  
    -   Utilisez le minutage de variable pour mettre en évidence d’importance. Par exemple, lors de la navigation dans une séquence d’éléments sur un diagramme de classes, permet d’accélérer le déplacement entre les transitions entre les éléments puis ralentir pour vous concentrer sur les éléments importants.  
  
-   **Utiliser l’accélération non linéaire progressive** d’un état à un autre, donner une idée de calme et physique mouvement  
  
-   Dans la mesure du possible, **utiliser une animation subtile pointage** pour indiquer les éléments interactifs sous la souris.  
  
-   Si vous reposent largement sur les animations dans vos fonctionnalités puis **fournissent un moyen de les mettre hors tension** localement (pour toutes les fonctionnalités) en tant qu’option dans le **Outils > Options** boîte de dialogue.  
  
-   **Qu’une seule animation doit se produire à la fois** et d’indiquer qu’un seul élément d’information.  
  
-   **Subtilité est importante.** Dans la plupart des cas, l’animation n’a à l’attention de l’utilisateur à la demande pour satisfaire à ses objectifs. Modifications subtiles dans la synchronisation, de séquencement et de comportement peuvent affecter considérablement la perception et peuvent faire la différence entre une animation efficace et inefficace.  
  
-   Lors de l’utilisation d’animation pour attirer l’attention sur quelque chose, **vous assurer qu’il est intéressant d’interrompre l’utilisateur**d’idée.  
  
-   **Lors de l’affichage de progression ou l’état** via animation :  
  
    -   Cesse d’afficher le déplacement de progression lorsque le processus sous-jacent n’est pas avancer.  
  
    -   Distinguer les processus indéterminés des processus déterminées.  
  
    -   Vérifiez qu’une animation identifiables États d’exécution et l’échec.  
  
    -   Réduire l’utilisation des animations d’effet qui indiquent l’état et vous assurer qu’une valeur réelle en fournissant des informations supplémentaires d’utilisation réelle. En cas d’urgence et les changements d’état temporaires sont des exemples  
  
#### <a name="do-not"></a>Ne pas :  
  
- Utilisez des mouvements de petits (déplacement dans un faible encombrement), préférant le fondu et change au fil du déplacement d’objets.  
  
- Utiliser des animations qui se produisent sur une large zone d’écran. Quelle que soit la taille, ce style d’animation est gênant l’utilisateur.  
  
- Utiliser des animations qui ne sont pas liées à l’objet de sur que l’utilisateur se concentre actuellement ou en interagissant avec.  
  
- Utiliser des animations qui nécessitent l’intervention de l’utilisateur de réinitialiser l’état, telles que de forcer l’utilisateur à répondre à une notification clignotante afin de la rendre arrêter clignotant. Interagir avec elles dans n’importe quel moyen devrait suffire faire disparaître les.  
  
  Pour plus d’informations sur les applications pour ces meilleures pratiques, consultez [modèles d’Animation](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Métriques d’animation  
  
-   Le système doit visiblement réagir aux mouvements de l’utilisateur en moins de 10 millisecondes.  
  
-   Transitions animées ne doivent pas durer plues de 500 millisecondes pour se terminer.  
  
-   La première consiste à compenser les transitions qui nécessitent des temps de plus de temps pour le séparer en deux parties ; par exemple, la première partie d’une animation peut être le conteneur de contenu vide (jusqu'à 500 millisecondes) suivi de l’atténuation de contenu dans le conteneur (jusqu'à 500 millisecondes).  
  
-   Pour les temps de chargement peuvent être calculés, un indicateur de progression déterminante (indicateur de progression de terminé en %) est préférable.  
  
-   Pour les temps de chargement qui ne peut pas être calculés, un indicateur d’occupation comme un curseur ou une animation en rotation embedded (chargement ou indicateur de travail) est approprié.  
  
### <a name="animation-as-communicator"></a>Animation en tant que communicator  
 Dans l’interface utilisateur de Visual Studio, l’animation fonctionne uniquement comme un outil de communication.  Il est utilisé pour communiquer une variété d’informations, telles que des modifications structurelles dans l’interface utilisateur ; par exemple, quand un menu s’ouvre ou ferme. Animation peut aider à visualiser le comportement dépendant du temps des systèmes complexes, telles que de la visualisation de progression d’installation ou être utilisée pour attirer l’attention des alertes et notifications.  
  
 Animations de l’interface utilisateur fonctionnent généralement de quatre manières : visualiser attirer votre attention, simuler et indiquer la réponse fois et cours.  
  
#### <a name="visualize"></a>Visualiser  
 Animation peut mettre l’accent sur la nature en trois dimensions d’objets et faciliter aux utilisateurs de visualiser leur structure spatiale. Pour ce faire, l’animation ont besoin pour mettre en place l’objet dans un cercle complet, lente de l’activer dans les deux sens, ou mettre l’objet plus proche et légèrement augmenter sa taille pour mettre en évidence une substitution ou le focus.  
  
 Bien que les objets en trois dimensions peuvent être déplacés avec le contrôle utilisateur, le concepteur doit déterminer à l’avance (par programmation ou manuellement) comment optimal animer un mouvement qui fournit une présentation optimale de l’objet. Cette programmées animation peut ensuite être activée par l’utilisateur en plaçant le curseur sur l’objet, tandis que les mouvements contrôlée par l’utilisateur nécessitent l’utilisateur à comprendre comment manipuler l’objet. Limiter le déplacement à un seul axe ou une orientation à la fois. mettre à l’échelle, faire pivoter, ou traduire, mais ne le faites pas plusieurs fois simultanément.  
  
 La catégorie de visualiser inclut les aspects de données, relations, état, structure, la séquence et temps.  
  
##### <a name="data"></a>Données  
 Illustrer des informations complexes et de variable :  
  
-   Naviguer entre les visualisations informations tels que les graphiques  
  
-   Pas à pas détaillé dans une séquence, la visite guidée et la pagination  
  
-   Appel de détails, pointant vers et mise en évidence des informations spécifiques  
  
-   Détails de la superposition et des informations supplémentaires sur un élément ayant le focus  
  
-   Transformation d’une représentation structurelle ou d’organisation à l’autre  
  
-   Représentant les modifications au fil du temps à l’aide de curseurs de temps, les roues jog et shuttle et contrôles de transport (lecture, arrêt et pause).  
  
##### <a name="relationships"></a>Relations  
  
-   Illustrent comment les éléments sont liés entre eux ou les éléments associés à un élément donné.  
  
-   Afficher les relations parent-enfant et hiérarchies ou les frères  
  
-   Un seul élément génère une autre  
  
-   Un seul élément réduit à un autre élément  
  
-   Un seul élément attaché à un autre  
  
##### <a name="state"></a>État  
  
-   Mises à jour de contenu.  
  
-   Sélection et le focus utilisateur  
  
-   Progression  
  
-   Erreurs  
  
##### <a name="structure"></a>Structure  
  
-   Glissement de la structure sur un nœud  
  
-   Réorientation  
  
-   Réduire et agrandir, ou développer et réduire  
  
##### <a name="sequence"></a>Séquence  
  
-   Séquence de diaporama  
  
-   Défiler les images  
  
##### <a name="time"></a>réflexion  
  
-   Afficher les modifications dans le temps, d’intervalle de temps et de capture vidéo  
  
-   Déplacer vers mettre, Annuler et rétablir  
  
-   Restaurer l’état de l’historique  
  
#### <a name="attract-attention"></a>Attirer votre attention  
 Si l’objectif est pour attirer l’attention de l’utilisateur en un seul élément hors plusieurs ou pour avertir l’utilisateur pour les informations mises à jour, une animation peut être appropriée. Par exemple, votre page de démarrage des applications peut-être utiliser un bouton de mise en route qui glisse en place une fois que la page se charge.  
  
 En règle générale, le dernier élément de déplacement sur l’écran attire l’attention des utilisateurs.  Dans une série d’éléments animés, attention de l’utilisateur suit le dernier objet mobile.  
  
##### <a name="alert"></a>Alerte  
  
-   Avertir l’utilisateur, l’attention, afficher la progression  
  
-   Afficher les que quelque chose est effectuée correctement ou non ou afficher la progression ou les modifications de la progression  
  
-   Demander aux utilisateurs lors d’une tâche, telles que la recherche d’informations en ligne ou en savoir plus sur la tâche actuelle  
  
##### <a name="notifications"></a>Notifications  
  
-   Alerter l’utilisateur sur une condition d’erreur  
  
-   Interrompre l’utilisateur pour voir s’il souhaite assister à quelque chose d’autre  
  
-   Doucement informe l’utilisateur un processus terminée ou qui a changé, tel que lorsqu’un téléchargement est terminé.  
  
#### <a name="simulate"></a>Simuler  
 Cette catégorie couvre physicality et dimensionnalité.  
  
-   Illustrer d'où proviennent les objets ou où ils accèdent à  
  
-   Développer et réduire ou ouvrir et fermer  
  
-   Panoramique, le défilement et la page active  
  
-   Empilement et l’ordre de plan  
  
-   Carrousel et accordion  
  
-   Retourner et faire pivoter l’interface utilisateur  
  
#### <a name="response-and-progress-indicators"></a>Indicateurs de réponse et de progression  
 Indicateurs de progression ont quelques avantages importants :  
  
-   Les deux indicateurs de progression déterminée et indéterminé rassurer l’utilisateur que le système n’est pas tombé en panne et travaille sur le problème.  
  
-   Indicateurs déterminées donner à l’utilisateur que la progression d’une idée de l’avancement de l’action, ainsi que d’un sentiment de plus proches de la fin.  
  
##  <a name="BKMK_AnimationPatterns"></a> Modèles d’animation  
  
### <a name="overview"></a>Vue d'ensemble  
 Les animations dans Visual Studio sont conçues pour répondre à une fonction spécifique et pas entraver la productivité des utilisateurs. Caractéristiques d’animation générales à respecter pour inclure :  
  
- Petites et discrète  
  
- Réalistes et naturelles  
  
- Subtils et tamisée  
  
- Rapide et efficace  
  
- Assouplie, pressé ou ne disposant ne pas  
  
  L’illustration suivante montre les styles d’animation recommandées pour une utilisation dans Visual Studio. Aucune animation et les animations subtiles comme apparition en ne fondu / fondu sont les plus fréquemment utilisés. Il existe une application limitée du déplacement des animations telles que développer et de contrat, X et Y position modification et la rotation.  
  
  ![Recommandé de styles d’animation pour Visual Studio](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")  
  
  **Styles d’animation recommandés pour Visual Studio**  
  
#### <a name="appear-and-disappear"></a>Apparaissent et disparaissent  
 Avec ce modèle, un élément bascule visible hors de la vue et revenir sans une animation de transition :  
  
 ![Apparaissent&#47;disparaissent animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")  
  
##### <a name="correct-usage"></a>Utilisation correcte  
 Éléments d’interface utilisateur fraîches qui doivent instantanément apparaissent ou disparaissent afin que l’utilisateur n’est ni distraits ni momentanément. En outre, les animations de déplacement lentes peuvent être perçues comme une opération de glissement de performances, ce qui n’a pas lieu avec le style s’affichent et disparaissent.  
  
##### <a name="incorrect-usage"></a>Utilisation incorrecte  
 Cas dans lesquels l’utilisateur n’a aucune idée brusquement, interface utilisateur s’affiche que s’est-il passé, et ajout d’une animation serait utile avec la compréhension contextuelle.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
 Le délai est généralement zéro seconde.  
  
##### <a name="examples"></a>Exemples  
  
-   Masquer les fenêtres Outil  
  
-   Interface utilisateur, telles que IntelliSense et aide sur les paramètres d’éditeur activés par le clavier  
  
-   Régions de code de développer et réduire  
  
#### <a name="fade-in-and-fade-out"></a>Apparition en fondu et fondu  
 Avec ce modèle, un élément d’interface utilisateur passe de non visible (opacité de 0 %) à visible (opacité de 100 %), ou vice versa :  
  
 ![Fondu&#45;dans&#47;fondu&#45;out animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")  
  
##### <a name="correct-usage"></a>Utilisation correcte  
 Ceci est le plus souvent recommandé animation de l’interface utilisateur. Il est un effet subtil qui ajoute un intérêt sans interrompre le flux. Dans certains cas, l’utilisateur peut même vous ne réalisiez pas qu’il est une animation et perçoit simplement un système de l’interface utilisateur sans heurts, flux.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Démarrage d’opacité : 0 % pour le fondu, 100 % pour le fondu  
  
-   Opacité de fin : 100 % pour le fondu, de 0 % pour le fondu  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
-   Style d’accélération : sinus InOut  
  
##### <a name="examples"></a>Exemples  
  
-   Masquer les fenêtres Outil  
  
-   Menu Ouvrir et fermer  
  
-   Transitions d’onglet en arrière-plan et de premier plan  
  
#### <a name="color-blend-from-a-to-b"></a>Mélange de couleurs de A à B  
 Avec ce modèle, un élément d’interface utilisateur change de couleur A par couleur b :  
  
 ![Mélange de couleurs animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")  
  
##### <a name="correct-usage"></a>Utilisation correcte  
 En tant qu’une transition animée lorsqu’un élément d’interface utilisateur change de couleur à partir d’un contexte ou état vers un autre.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Couleur de début : interface utilisateur spécifique  
  
-   Couleur de fin : interface utilisateur spécifique  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
-   Style d’accélération : sinus InOut  
  
##### <a name="examples"></a>Exemples  
  
-   Transitions d’état de fenêtre de document (active, la dernière actives et inactives)  
  
-   Transitions d’état de fenêtre d’outils (ayant le focus et inactif)  
  
#### <a name="expand-and-contract"></a>Être accrus ou réduits  
 Avec ce modèle, un élément d’interface utilisateur se développe dans X, Y ou les deux sens :  
  
 ![Développez&#47;contrat animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")  
  
##### <a name="correct-usage"></a>Utilisation correcte  
 En tant qu’une transition animée lorsqu’un élément d’interface utilisateur modifie la taille d’un contexte à un autre.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Échelle x : % ou une dimension spécifique (en pixels)  
  
-   Mise à l’échelle Y : % ou une dimension spécifique (en pixels)  
  
-   Position de l’ancrage : en règle générale supérieur gauche (pour les langues de gauche à droite) ou supérieur droit (pour les langues de droite à gauche)  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
##### <a name="examples"></a>Exemples  
  
-   Volet d’Explorateur de l’architecture développer / réduire  
  
-   Élément de Page de démarrage développer / réduire  
  
#### <a name="x-y-position-change"></a>X-Y positionner la modification  
 Avec ce modèle, un élément d’interface utilisateur change sa position X ou Y ou les deux :  
  
 ![X&#47;position Y modifier l’animation dans Visual Studio](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")  
  
##### <a name="correct-usage"></a>Utilisation correcte  
 En tant qu’une transition animée lorsqu’un élément d’interface utilisateur change de position d’un contexte à un autre.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Position à partir de X et Y : interface utilisateur spécifique  
  
-   Position de fin de X et Y : interface utilisateur spécifique  
  
-   Chemin d’accès de mouvement : aucun  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
-   Style d’accélération : sinus InOut  
  
##### <a name="example"></a>Exemple  
 Réorganisation de l’onglet  
  
#### <a name="rotate"></a>Faire pivoter  
 Avec ce modèle, l’élément d’interface utilisateur fait pivoter :  
  
 ![Animation faire pivoter dans Visual Studio](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")  
  
##### <a name="correct-usage"></a>Utilisation correcte  
 Uniquement pour l’indicateur de progression en rotation indéterminé.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Degré de rotation : 360  
  
-   Centre de rotation : central de l’objet  
  
-   Durée : continue  
  
##### <a name="example"></a>Exemple  
 Indicateur de progression indéterminée (rotation)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Les actions de l’interface utilisateur shell courantes et les animations recommandées  
  
#### <a name="tab-open"></a>Onglet ouvert  
  
- Style : apparaissent  
  
- Durée : Zéro seconde  
  
  ![Onglet animation ouvrir dans Visual Studio](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")  
  
#### <a name="tab-close"></a>Onglet fermer  
  
- Style : Changer de position X  
  
- Durée : 200 millisecondes  
  
  ![Onglet animation Fermer dans Visual Studio](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")  
  
#### <a name="tab-reorder"></a>Réorganisation de l’onglet  
  
- Style : Changer de position X  
  
- Durée : 200 millisecondes  
  
  ![Onglet animation réorganiser dans Visual Studio](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")  
  
#### <a name="close-floating-document"></a>Fermer le document flottante  
  
- Style : apparaissent  
  
- Durée : 200 millisecondes  
  
  ![Fermer flottante d’animation de document dans Visual Studio](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")  
  
#### <a name="window-state-transition"></a>Transition d’état de fenêtre  
  
- Style : Pour garantir une cohérence avec d’autres fenêtres, permettent du système d’exploitation actuel définir l’animation de fermeture du document.  
  
- Durée : 200 millisecondes  
  
  ![Animation de transition d’état fenêtre dans Visual Studio](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")  
  
#### <a name="menu-open"></a>Menu Ouvrir  
  
- Style : fondu  
  
- Durée : 200 millisecondes  
  
  ![Animation ouvrir le menu dans Visual Studio](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")  
  
#### <a name="menu-close"></a>Menu fermer  
  
- Style : fondu  
  
- Durée : 200 millisecondes  
  
  ![Animation fermer le menu dans Visual Studio](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")  
  
#### <a name="auto-hide-tool-window-reveal"></a>Divulgation de fenêtre outil de masquage automatique  
  
- Style : apparaissent  
  
- Durée : Zéro seconde  
  
  ![Auto&#45;masquer l’animation de la fenêtre outil dans Visual Studio](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")

