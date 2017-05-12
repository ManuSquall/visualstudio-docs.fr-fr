---
title: Animations pour Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: b36b5e35758ad10109328d6f001e043ad7dcbe15
ms.contentlocale: fr-fr
ms.lasthandoff: 05/04/2017

---
# <a name="animations-for-visual-studio"></a>Animations pour Visual Studio
## <a name="animation-fundamentals"></a>Notions de base de l’animation  
  
### <a name="animation-best-practices-in-visual-studio"></a>Meilleures pratiques de l’animation dans Visual Studio  
Suivez ces règles pour vous assurer de styles d’animation cohérente et conviviale dans l’IDE de Visual Studio.  
  
-   **Soyez sélectif.** Limiter les animations à celles qui remplissent une fonction spécifique.  
  
-   **Minutage et vitesse sont importants** pour vous assurer que les transitions se sentir rapide et naturelle :  
  
    -   Effectuer des transitions animées au sein d’une demi-seconde (500 millisecondes).  
  
    -   Les animations qui se produisent fréquemment doivent être suffisamment rapide pour qu’elles n’interrompront pas le flux de travail de l’utilisateur. Surveiller l’animation dans une boucle et ajuster la durée jusqu'à ce qu’il semble correct. 
  
    -   Animations ne doivent pas être donc rapide ou glacial qu’il est difficile à comprendre, mais pas tellement lent qu’elle effectue un impatiente pour la transition se termine.  
  
    -   Utilisez la minuterie de variable pour souligner l’importance. Par exemple, lorsque vous naviguez à travers une séquence d’éléments sur un diagramme de classes, accélérer via les transitions entre les éléments, puis ralentir pour vous concentrer sur des éléments importants.  
  
-   **Utiliser l’accélération non linéaire progressive** d’un état à un autre, en donnant un sens de circulation calme et naturelle.  
  
-   Lorsque cela est possible, **utiliser une animation subtile pointage** pour indiquer les éléments interactifs sous la souris.  
  
-   Si vous reposent largement sur des animations dans vos fonctionnalités, puis **fournissent un moyen de les mettre hors tension** localement (pour toutes les fonctionnalités) en tant qu’option dans le **Outils > Options** boîte de dialogue.  
  
-   **Seul l’animation doit se produire à la fois** et d’indiquer qu’un seul élément d’information. Plusieurs objets de déplacement ou la tentative de transmettre plusieurs choses peuvent prêter à confusion. 
  
-   **Plusieurs est important.** Dans la plupart des cas, l’animation ne doit pas nécessairement attention de l’utilisateur à la demande pour assumer son rôle. Modifications subtiles apportées dans le délai, de mise en séquence et de comportement peuvent affecter considérablement la perception et peuvent faire la différence entre une animation efficace et inefficace.  
  
-   Lors de l’utilisation d’animation pour attirer l’attention sur quelque chose, **vous assurer qu’il est intéressant d’interrompre l’utilisateur**d’effectuer l’apprentissage de la réflexion.  
  
-   **Lors de l’affichage d’état ou progression** via l’animation :  
  
    -   Arrêter montrant le mouvement de progression lorsque le processus sous-jacent n’est pas avancer. 
  
    -   Distinguer les processus indéterminés des processus déterminés.  
  
    -   Vérifiez que les États d’exécution et l’échec identifiables une animation.  
  
    -   Réduire l’utilisation des animations d’effet qui indiquent l’état et de vous assurer qu’ils disposent la valeur réelle en fournissant des informations supplémentaires d’utilisation réelle. Exemples de situations d’urgence et de changement d’état transitoire  
  
#### <a name="animation-donts"></a>Avertissements d’animation :
  
-   N’utilisez pas petits mouvements (déplacement dans un faible encombrement mémoire). Préférez fondus et change au fil du déplacement d’objets.  
  
-   N’utilisez pas les animations qui ont lieu sur une large zone de surface. Quelle que soit la taille, ce style d’animation est inutiles à l’utilisateur.  
  
-   N’utilisez pas les animations sans rapport avec l’objet de de que l’utilisateur est en train ou en interagissant avec.  
  
-   N’utilisez pas les animations qui nécessitent l’intervention de l’utilisateur de réinitialiser l’état, telles que de forcer l’utilisateur à répondre à une notification clignotante pour qu’il arrête de clignoter. Interagir avec elles en aucune façon doit être suffisante pour les ignorer.  
  
Pour plus d’informations sur les applications pour ces meilleures pratiques, consultez [modèles d’Animation](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Métriques d’animation  
  
-   Le système doit visiblement réagir aux mouvements de l’utilisateur en moins de 10 millisecondes.  
  
-   Des transitions animées ne doivent pas prendre plues de 500 millisecondes pour terminer.  
  
-   Un pour compenser les transitions qui nécessitent des durées consiste à séparer en deux parties. Par exemple, la première partie d’une animation peut être le conteneur de contenu vide (jusqu'à 500 millisecondes), suivi de l’atténuation de contenu dans le conteneur (jusqu'à 500 millisecondes).  
  
-   Pour les temps de chargement qui peuvent être calculées, un indicateur de progression déterminante (indicateur de progression de fait en %) est préféré.  
  
-   Pour les temps de chargement qui ne peut pas être calculés, un indicateur de disponibilité comme un curseur ou d’une animation tournant incorporé (chargement ou indicateur du travail) est approprié.  
  
### <a name="animation-as-communicator"></a>Animation comme communicator  
Dans l’interface utilisateur de Visual Studio, l’animation fonctionne uniquement comme un outil de communication.  Il est utilisé pour communiquer une variété d’informations, telles que des modifications structurelles dans l’interface utilisateur (par exemple, lorsqu’un menu ouvre ou ferme). Animation peut aider à visualiser le comportement dépendant du temps des systèmes complexes, comme la visualisation de progression de l’installation. Animations peuvent également servir à attirer l’attention des alertes et notifications.  
  
 Les animations de l’interface utilisateur fonctionnent généralement de quatre façons : visualiser, attirer l’attention, simuler, et les heures de réponse/indicateurs de progression.  
  
#### <a name="visualize"></a>Visualiser  
Animation peut mettent l’accent sur la nature à trois dimensions d’objets et le rendre plus facile à visualiser leur structure spatiale. Pour ce faire, l’animation ont besoin pour faire pivoter l’objet dans un cercle complet, à variation lente de l’activer dans les deux sens, ou mettre l’objet plus proche et légèrement augmenter sa taille pour mettre en évidence le focus ou substitution.  
  
Bien que les objets en trois dimensions peuvent être déplacés avec le contrôle utilisateur, le concepteur doit déterminer à l’avance (par programmation ou manuellement) comment au mieux animer un mouvement qui fournit un fonctionnement optimal de l’objet. Cette option programmé animation peut ensuite être activée par l’utilisateur en plaçant le curseur sur l’objet, tandis que les mouvements de contrôlée par l’utilisateur nécessite que l’utilisateur à comprendre comment manipuler l’objet. Limiter le déplacement à un seul axe ou à l’orientation à la fois. mettre à l’échelle, faire pivoter, ou traduire, mais ne le faites pas plusieurs simultanément.  
  
La catégorie de visualiser inclut les aspects des données, relations, état, structure, séquence et heure.  
  
##### <a name="data"></a>Données  
Illustrent informations complexes et de variable :  
  
-   Naviguer entre les visualisations des informations telles que des graphiques  
  
-   Pas à pas détaillé dans une séquence, la visite guidée et la pagination  
  
-   Appel de détails, en pointant et mise en évidence des informations spécifiques  
  
-   Recouvrir des détails et des informations supplémentaires sur un élément ayant le focus
  
-   Transformation d’une représentation structurelle ou d’organisation à l’autre  
  
-   Représentant les modifications au fil du temps à l’aide de curseurs de temps, ligne brisée et navette roues et les contrôles de transport (lecture, arrêt et pause) 
  
##### <a name="relationships"></a>Relations  
  
-   Illustrer comment éléments sont liés entre eux ou les éléments qui sont liés à un élément donné
  
-   Afficher les relations parent-enfant et hiérarchies ou un frère
  
-   Un seul élément génère une autre
  
-   Un élément est réduit à un autre élément
  
-   Un seul élément attaché à un autre
  
##### <a name="state"></a>État  
  
-   Les mises à jour
  
-   Sélection et le focus utilisateur  
  
-   Progression  
  
-   Errors  
  
##### <a name="structure"></a>Structure  
  
-   Glissement de la structure d’un nœud  
  
-   Réorientation  
  
-   Réduire et agrandir, ou développer et réduire  
  
##### <a name="sequence"></a>Séquence  
  
-   Séquence de diaporama  
  
-   Retournement d’images  
  
##### <a name="time"></a>réflexion  
  
-   Afficher les modifications dans le temps, d’intervalle de temps et de capture  
  
-   Déplacer vers la Corbeille, Annuler et rétablir  
  
-   Restaurer l’état de l’historique  
  
#### <a name="attract-attention"></a>Attirer l’attention  
Si l’objectif est pour attirer l’attention de l’utilisateur à un seul élément hors plusieurs ou pour avertir l’utilisateur pour les informations mises à jour, une animation peut être appropriée. Par exemple, votre page de démarrage d’application peut utiliser un bouton de mise en route diapositives en place une fois le chargement de la page.  
  
En règle générale, le dernier élément mobile sur l’écran d’attire l’attention des utilisateurs.  Dans une série d’éléments animés, l’attention des utilisateurs suit le dernier objet mobile.  
  
##### <a name="alert"></a>Alerte  
  
-   Avertir l’utilisateur, l’attention, afficher la progression  
  
-   Afficher que quelque chose est effectuée correctement ou progression ou les modifications de la progression  
  
-   Demander aux utilisateurs pendant une tâche, telles que la recherche d’informations en ligne ou en savoir plus sur la tâche en cours  
  
##### <a name="notifications"></a>Notifications  
  
-   Alerte de l’utilisateur sur une condition d’erreur  
  
-   Interruption de l’utilisateur pour voir s’il souhaite participer à un autre  
  
-   Doucement informe les utilisateurs qu’un processus est terminé ou modifié, comme lors d’un téléchargement est terminé.  
  
#### <a name="simulate"></a>Simuler  
Cette catégorie couvre physicality et dimensionnalité.  
  
-   Illustrer d'où proviennent les objets ou où elles sont placées à  
  
-   Développer et réduire ou ouvrir et fermer  
  
-   Panoramique, le défilement et la page active  
  
-   Empilement et l’ordre de plan  
  
-   Carrousel et Accordéon  
  
-   Retourner et faire pivoter l’interface utilisateur  
  
#### <a name="response-and-progress-indicators"></a>Indicateurs de réponse et la progression  
Indicateurs de progression ont quelques avantages importants :  
  
-   Les deux indicateurs de progression déterminée et indéterminé expliquant l’utilisateur que le système n’est pas tombé en panne et fonctionne sur le problème.  
  
-   Indicateurs déterminées donnent à l’utilisateur que la progression d’une idée de l’avancement de l’action, ainsi que d’un sentiment de plus proches de la fin.  
  
##  <a name="BKMK_AnimationPatterns"></a>Modèles d’animation  
  
### <a name="overview"></a>Vue d'ensemble  
Animations dans Visual Studio sont conçues pour répondre à une fonction spécifique sans affecter négativement la productivité des utilisateurs. En règle générale, les animations dans Visual Studio doivent être :  
  
-   Légère et  
  
-   Réalistes et naturelles  
  
-   Subtils et suppression  
  
-   Rapide et efficace  
  
-   Ne pas d’accélérée allégées  
  
Cette illustration montre les styles d’animation que nous recommandons pour Visual Studio. Aucune animation ou animations subtiles comme fondu / disparition en fondu ne sont les plus fréquemment utilisées. Est une application limitée d’animations de mouvement comme croître et réduire, positions X et Y modifier et rotation. 
  
![Styles d’animation recommandés pour Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Styles d'animation recommandés pour Visual Studio
  
#### <a name="appear-and-disappear"></a>Apparaissent et disparaissent  
Avec ce modèle, un élément bascule visible hors de vue et sans une animation de la transition.  
  
![Apparaissent et disparaissent d’animation](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Apparaissent et disparaissent d’animation  
  
##### <a name="correct-usage"></a>Utilisation correcte  
Éléments d’interface utilisateur actualisées qui doivent instantanément apparaissent ou disparaissent afin que l’utilisateur n’est ni distraits ni coupé. En outre, des animations lente peuvent être perçues comme un opération glisser de performances, qui ne se produise avec le style apparaissent et disparaissent.  
  
##### <a name="incorrect-usage"></a>Utilisation incorrecte  
Cas dans lequel l’interface utilisateur apparaît soudain de que l’utilisateur ne sait pas que s’est-il passé et ajout d’une animation aider à la compréhension contextuelle.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
Le délai est généralement zéro.  
  
##### <a name="examples"></a>Exemples    
-   Masquer les fenêtres Outil  
  
-   Interface utilisateur, telles qu’IntelliSense et l’aide sur les paramètres d’éditeur activés par le clavier  
  
-   Régions de développer et réduire le code  
  
#### <a name="fade-in-and-fade-out"></a>Fondu avant et arrière  
Avec ce modèle, un élément d’interface utilisateur passe à partir de n’est pas visible (0 % d’opacité) visible (opacité de 100 %), ou vice versa.  
  
![Animation fondu avant et arrière](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Animation fondu avant et arrière  
  
##### <a name="correct-usage"></a>Utilisation correcte  
Cela est recommandé les plus couramment d’animation de l’interface utilisateur. Il s’agit d’un effet subtil qui ajoute un intérêt sans interrompre le flux. Dans certains cas, l’utilisateur ne réalisez pas qu’il existe une animation, percevoir une lisse et de passage de système de l’interface utilisateur.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Démarrage d’opacité : 0 % pour apparaître progressivement, 100 % pour disparaître progressivement  
  
-   Opacité de fin : 100 % pour apparaître progressivement, de 0 % pour disparaître progressivement  
  
-   Durée : 200 millisecondes autonome, les 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
-   Accélération de style : sinus InOut  
  
##### <a name="examples"></a>Exemples  
  
-   Masquer les fenêtres Outil  
  
-   Menu Ouvrir et fermer  
  
-   Transitions onglet en arrière-plan et de premier plan  
  
#### <a name="color-blend-from-a-to-b"></a>Mélange de couleurs de A à B  
Avec ce modèle, un élément d’interface utilisateur change de couleur A par couleur B.  
  
![Animation mélange de couleurs](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Animation mélange de couleurs  
  
##### <a name="correct-usage"></a>Utilisation correcte  
En tant qu’une transition animée lorsqu’un élément d’interface utilisateur change de couleur à partir d’un contexte ou état vers un autre.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Couleur de début : l’interface utilisateur spécifique  
  
-   Couleur de fin : l’interface utilisateur spécifique  
  
-   Durée : 200 millisecondes autonome, les 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
-   Accélération de style : sinus InOut  
  
##### <a name="examples"></a>Exemples  
  
-   Transitions d’état de fenêtre de document (actif, la dernière actives et inactives)  
  
-   Outil de transitions d’état de fenêtre (ayant le focus et inactif)  
  
#### <a name="expand-and-contract"></a>Développez et un contrat  
Avec ce modèle, un élément d’interface utilisateur développe dans X, Y ou les deux sens.  
  
![Développez et un contrat d’animation](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Développez et un contrat d’animation  
  
##### <a name="correct-usage"></a>Utilisation correcte  
En tant qu’une transition animée lorsqu’un élément d’interface utilisateur modifie la taille d’un contexte à un autre.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Échelle x : % ou une dimension spécifique (en pixels)  
  
-   Échelle Y : % ou une dimension spécifique (en pixels)  
  
-   Position de l’ancrage : généralement supérieur gauche (pour les langues de gauche à droite) ou supérieur droit (pour les langues de droite à gauche)  
  
-   Durée : 200 millisecondes autonome, les 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
##### <a name="examples"></a>Exemples  
  
-   Panneau de l’Explorateur d’architecture développer / réduire  
  
-   Élément de développer et réduire de Page de démarrage  
  
#### <a name="x-y-position-change"></a>X-Y placer des modifications  
Avec ce modèle, un élément d’interface utilisateur change sa position X ou Y ou les deux.  
  
![Animation de modification de position X-Y](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />Animation de modification de position X-Y  
  
##### <a name="correct-usage"></a>Utilisation correcte  
En tant qu’une transition animée lorsqu’un élément d’interface utilisateur change de position d’un contexte à un autre.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Position à partir de X et Y : l’interface utilisateur spécifique  
  
-   Position de fin de X et Y : l’interface utilisateur spécifique  
  
-   Trajectoire : aucun  
  
-   Durée : 200 millisecondes autonome, les 100 millisecondes lorsqu’il est utilisé en tant que partie d’une séquence d’animation de combinaison  
  
-   Accélération de style : sinus InOut  
  
##### <a name="example"></a>Exemple  
Réorganisation de l’onglet  
  
#### <a name="rotate"></a>Faire pivoter  
Avec ce modèle, l’élément d’interface utilisateur fait pivoter.  
  
![Animation de rotation de l’interface utilisateur élément](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Animation de rotation de l’interface utilisateur élément  
  
##### <a name="correct-usage"></a>Utilisation correcte  
Uniquement pour l’indicateur de progression en rotation indéterminé.  
  
##### <a name="animation-properties"></a>Propriétés de l’animation  
  
-   Degré de rotation : 360  
  
-   Centre de rotation : au milieu de l’objet  
  
-   Durée : continue  
  
##### <a name="example"></a>Exemple  
Indicateur de progression indéterminée (rotation)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Les actions d’interface utilisateur shell courantes et les animations recommandées  
  
#### <a name="tab-open"></a>Onglet ouvert  
![Animation ouvrir l’onglet](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Animation ouvrir l’onglet  
    
-   Style : apparaissent  
  
-   Durée : zéro seconde  

#### <a name="tab-close"></a>Onglet fermer  
![Animation fermer l’onglet](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Animation fermer l’onglet  
  
-   Style : Modification de la position X  
  
-   Durée : 200 millisecondes  
  
#### <a name="tab-reorder"></a>Onglet commande  
![Animation réorganiser l’onglet dans Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Animation réorganiser l’onglet

-   Style : Modification de la position X  
  
-   Durée : 200 millisecondes  
    
#### <a name="close-floating-document"></a>Fermer document flottante  
![Animation de document flottante fermer](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Animation de document flottante fermer  
   
-   Style : apparaissent  
  
-   Durée : 200 millisecondes   
 
#### <a name="window-state-transition"></a>Transition d’état de fenêtre  
![Animations de transition d’état fenêtre](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Animations de transition d’état fenêtre  
    
-   Style : pour être cohérent avec d’autres fenêtres, permettent de système d’exploitation définissent l’animation de fermeture du document.  
  
-   Durée : 200 millisecondes  
  
#### <a name="menu-open"></a>Menu Ouvrir  
![Animation ouvrir le menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Animation ouvrir le menu  
    
-   Style : fondu  
  
-   Durée : 200 millisecondes  
  
#### <a name="menu-close"></a>Fermer le menu  
![Animation fermer le menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Animation fermer le menu  
    
-   Style : fondu  
  
-   Durée : 200 millisecondes  
  
#### <a name="auto-hide-tool-window-reveal"></a>Masquer automatiquement révéler de fenêtre outil  
![Masquer automatiquement l’animation de révéler la fenêtre outil](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Masquer automatiquement l’animation de révéler la fenêtre outil  

-   Style : apparaissent  
  
-   Durée : zéro seconde
