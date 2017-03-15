---
title: "Animations pour Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Animations pour Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Principes de base de l'animation  
  
### Meilleures pratiques de l'animation dans Visual Studio  
 Suivez ces règles pour vous assurer de styles d'animation cohérente et conviviale sur l'IDE de Visual Studio.  
  
-   **Soyez sélectif.** Limiter les animations à ceux qui servent à des fins spécifiques.  
  
-   **Minutage et vitesse sont importantes** pour vous assurer que les transitions se sentent rapide et naturelle :  
  
    -   Effectuer des transitions animées au sein d'une demi\-seconde \(500 millisecondes\).  
  
    -   Les animations qui se produisent fréquemment doivent être suffisamment rapide pour qu'elles n'interrompront pas le flux de travail de l'utilisateur.  
  
    -   Animations ne doivent pas être tellement rapide ou souffrent qu'il est difficile à comprendre, mais pas tellement lent qu'elle effectue un impatiente de la transition se termine.  
  
    -   Utilisez la minuterie variable pour souligner l'importance. Par exemple, lorsque vous naviguez à travers une séquence d'éléments sur un diagramme de classes, accélérer via les transitions entre les éléments, puis ralentir pour vous concentrer sur les éléments importants.  
  
-   **Utiliser l'accélération linéaire progressive** d'un état à un autre, donnant un sens de mouvement calme et naturels  
  
-   Lorsque cela est possible, **utiliser une animation subtile pointage** pour indiquer les éléments interactifs sous la souris.  
  
-   Si vous dépendez largement des animations dans vos fonctionnalités puis **fournissent un moyen de les mettre hors tension** localement \(pour toutes les fonctionnalités\) en tant qu'option dans le **Outils \> Options** boîte de dialogue.  
  
-   **Qu'une animation doit se produire à la fois** et d'indiquer qu'un seul élément d'information.  
  
-   **Subtilité est importante.** Dans la plupart des cas, l'animation n'à l'attention de l'utilisateur à la demande pour assumer son rôle. Modifications subtiles minutage séquencement et comportement peuvent affecter considérablement la perception et peuvent faire la différence entre une animation efficace et inefficace.  
  
-   Lors de l'utilisation de l'animation à attirer l'attention sur quelque chose, **vous assurer qu'il est intéressant d'interrompre l'utilisateur**d'idée.  
  
-   **Lors de l'affichage de progression ou l'état** via l'animation :  
  
    -   Arrêter d'afficher les mouvements de progression lorsque le processus sous\-jacent n'est pas avancer.  
  
    -   Distinguer les processus indéterminés des processus déterminés.  
  
    -   Assurez\-vous que les États d'exécution et l'échec identifiables une animation.  
  
    -   Pour réduire l'utilisation des animations effet qui indiquent l'état et assurez\-vous d'avoir une valeur réelle en fournissant des informations supplémentaires d'utilisation réelle. Exemples de situations d'urgence et des changements d'état transitoire  
  
#### Ne pas faire :  
  
-   Utilisez des mouvements de petites \(mouvement dans un faible encombrement mémoire\), préférant fondus et change au fil du déplacement d'objets.  
  
-   Utiliser des animations qui ont lieu sur une large zone de l'écran. Quelle que soit la taille, ce style d'animation est inutiles à l'utilisateur.  
  
-   Utiliser des animations qui ne sont pas liées à l'objet de sur que l'utilisateur se concentre actuellement ou en interagissant avec.  
  
-   Utiliser des animations qui nécessitent l'intervention de l'utilisateur de réinitialiser l'état, telles que de forcer l'utilisateur à répondre à une notification pour qu'il arrête de clignoter clignotante. Interagir avec eux en aucune façon doit être suffisante pour faire disparaître les.  
  
 Pour plus d'informations sur les applications pour ces meilleures pratiques, consultez [Modèles d'animation](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### Mesures d'animation  
  
-   Le système doit visiblement réagir aux mouvements de l'utilisateur en moins de 10 millisecondes.  
  
-   Transitions animées ne doivent pas durer plues de 500 millisecondes pour se terminer.  
  
-   La première consiste à compenser les transitions qui nécessitent des temps de pour le séparer en deux parties ; par exemple, la première partie d'une animation peut être le conteneur de contenu vide \(jusqu'à 500 millisecondes\) suivi de l'atténuation de contenu dans le conteneur \(jusqu'à 500 millisecondes\).  
  
-   Pour les temps de chargement peuvent être calculés, un indicateur de progression déterminante \(indicateur de progression %\-terminé\) est préférable.  
  
-   Pour les temps de chargement qui ne peut pas être calculés, un indicateur de disponibilité tel qu'un curseur ou d'une animation de rotation incorporé \(chargement ou indicateur de travail\) est approprié.  
  
### Animation que communicator  
 Dans l'interface utilisateur de Visual Studio, l'animation fonctionne uniquement comme un outil de communication.  Il est utilisé pour communiquer une variété d'informations, telles que des modifications structurelles dans l'interface utilisateur ; par exemple, quand un menu ouvre ou ferme. L'animation peut aider à visualiser le comportement dépendant du temps des systèmes complexes, tels que de la visualisation de progression d'installation ou servir à attirer l'attention des alertes et des notifications.  
  
 Animations de l'interface utilisateur fonctionnent généralement de quatre manières : visualiser, attirer l'attention, simuler et indiquer la réponse fois\/progression.  
  
#### Visualiser  
 Animation peut mettre l'accent sur la nature des objets en trois dimensions et rendre plus faciles à visualiser leur structure spatiale. Pour ce faire, l'animation ont besoin pour faire pivoter l'objet dans un cercle complet, lentement l'activer dans les deux sens, ou mettre l'objet plus proche et légèrement augmenter sa taille pour mettre en évidence le focus ou substitution.  
  
 Bien que les objets en trois dimensions peuvent être déplacés avec le contrôle utilisateur, le concepteur doit déterminer à l'avance \(par programmation ou manuellement\) comment optimal animer un mouvement qui fournit un fonctionnement optimal de l'objet. Cette programmé animation peut ensuite être activée par l'utilisateur en plaçant le curseur sur l'objet, tandis que les mouvements contrôlée par l'utilisateur que l'utilisateur de comprendre comment manipuler l'objet. Limiter le mouvement à un seul axe ou à l'orientation à la fois. mettre à l'échelle, faire pivoter, ou traduire, mais ne faites pas plusieurs fois simultanément.  
  
 La catégorie de visualiser inclut les aspects de données, relations, état, structure, la séquence et temps.  
  
##### Données  
 Illustrent informations complexes et de variable :  
  
-   Naviguer entre des visualisations informations tels que les graphiques  
  
-   Pas à pas détaillé dans une séquence, la visite guidée et la pagination  
  
-   Appel de détails, en pointant et mise en évidence des informations spécifiques  
  
-   Détails de la superposition et des informations supplémentaires sur un élément ayant le focus  
  
-   Transformation d'une représentation structurelle ou organisation à l'autre  
  
-   Représentant les modifications au fil du temps à l'aide de curseurs de temps, ligne brisée et navette roues et les contrôles de transport \(lecture, arrêt et pause\).  
  
##### Relationships  
  
-   Illustre l'interaction avec les éléments entre eux ou les éléments associés à un élément donné.  
  
-   Afficher les relations parent\-enfant et hiérarchies ou les frères  
  
-   Un seul élément génère une autre  
  
-   Un seul élément est réduit à un autre élément  
  
-   Un seul élément attaché à un autre  
  
##### État  
  
-   Mises à jour de contenu.  
  
-   Sélection et l'orientation de l'utilisateur  
  
-   Progression  
  
-   Erreurs  
  
##### Structure  
  
-   Glissement de la structure sur un nœud  
  
-   Réorientation  
  
-   Réduire et agrandir, ou développer \/ réduire  
  
##### Séquence  
  
-   Séquence de diaporama  
  
-   Retournement d'images  
  
##### Heure  
  
-   Afficher les modifications dans le temps, d'intervalle de temps et de capture vidéo  
  
-   Déplacer vers les déchets, Annuler et rétablir  
  
-   Historique de l'état de restauration  
  
#### Attirer l'attention  
 Si l'objectif consiste à attirer l'attention de l'utilisateur sur un seul élément hors plusieurs ou à alerter l'utilisateur pour les informations mises à jour, une animation peut être appropriée. Par exemple, votre page de démarrage d'applications peut\-être utiliser un bouton de mise en route des diapositives en place une fois le chargement de la page.  
  
 En règle générale, le dernier élément de déplacement à l'écran attire l'attention des utilisateurs.  Dans une série d'éléments animés, l'attention des utilisateurs suit le dernier objet mobile.  
  
##### Alerte  
  
-   Avertir l'utilisateur, l'attention, afficher la progression  
  
-   Afficher que quelque chose est effectuée correctement ou afficher la progression ou les modifications de la progression  
  
-   Inviter les utilisateurs lors d'une tâche, telles que la recherche d'informations en ligne ou en savoir plus sur la tâche en cours  
  
##### Notifications  
  
-   Alerter l'utilisateur sur une condition d'erreur  
  
-   Interrompre l'utilisateur pour voir s'il souhaite participer à un autre  
  
-   Doucement informer l'utilisateur qu'un processus a terminé ou modifié, par exemple lorsqu'un téléchargement est terminé.  
  
#### Simuler  
 Cette catégorie couvre physicality et dimensionnalité.  
  
-   Illustrer d'où proviennent les objets ou où elles accèdent à  
  
-   Développer et réduire ou ouvrir et fermer  
  
-   Panoramique, le défilement et la page active  
  
-   Empilement et positionnement z  
  
-   Carrousel et Accordéon  
  
-   Retourner et faire pivoter l'interface utilisateur  
  
#### Indicateurs de progression et de réponse  
 Indicateurs de progression ont plusieurs avantages importants :  
  
-   Les deux indicateurs de progression déterminée et indéterminé rassurer l'utilisateur que le système n'est pas tombé en panne et qu'il fonctionne sur le problème.  
  
-   Indicateurs déterminées donner à l'utilisateur qu'une idée de l'avancement de l'action est en cours de traitement, ainsi qu'un sentiment de plus proches de la fin.  
  
##  <a name="BKMK_AnimationPatterns"></a> Modèles d'animation  
  
### Vue d'ensemble  
 Animations dans Visual Studio sont conçues pour répondre à une fonction spécifique et pas entraver la productivité des utilisateurs. Caractéristiques d'animation générales à respecter pour inclure :  
  
-   Légère et  
  
-   Réalistes et naturelles  
  
-   Subtils et suppression  
  
-   Rapide et efficace  
  
-   Souple, pas constaté.  
  
 L'illustration suivante montre les styles d'animation recommandées pour une utilisation dans Visual Studio. Aucune animation et les animations subtiles comme ne fondu \/ fondu sont les plus fréquemment utilisées. Est une application limitée du déplacement des animations comme augmente ou diminue, positions X et Y modifier et rotation.  
  
 ![Recommended animation styles for Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202\-a\_VSAnimStyles")  
  
 **Styles d'animation recommandés pour Visual Studio**  
  
#### Apparaître et disparaître  
 Avec ce modèle, un élément de bascule de visibles hors de vue et sans une animation de transition :  
  
 ![Appear&#47;Disappear animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202\-b\_AppearAndDisappear")  
  
##### Utilisation correcte  
 Éléments d'interface utilisateur actualisées devant instantanément apparaissent ou disparaissent afin que l'utilisateur n'est ni distraits ni coupé. En outre, les animations de déplacement lentes peuvent être perçues comme une opération de glissement de performances qui ne se produise avec le style apparaissent et disparaissent.  
  
##### Utilisation incorrecte  
 Cas dans lequel l'interface utilisateur apparaît soudain de que l'utilisateur n'a aucune idée que s'est\-il passé et ajout d'une animation serait utile avec une compréhension contextuelle.  
  
##### Propriétés de l'animation  
 Le délai d'exécution n'est généralement zéro seconde.  
  
##### Exemples  
  
-   Masquer les fenêtres Outil  
  
-   Interface utilisateur, telles que IntelliSense et l'aide sur les paramètres d'éditeur activés par le clavier  
  
-   Régions de code de développer et réduire  
  
#### Fondu et fondu  
 Avec ce modèle, un élément d'interface utilisateur passe de non visibles \(0 % d'opacité\) visible \(100 % d'opacité\) ou vice versa :  
  
 ![Fade&#45;in&#47;Fade&#45;out animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202\-c\_FadeInFadeOut")  
  
##### Utilisation correcte  
 Ceci est le plus souvent recommandé animation de l'interface utilisateur. Il est un effet subtil qui ajoute un intérêt sans interrompre le flux. Dans certains cas, l'utilisateur peut conscience qu'il correspond à une animation et perçoit simplement un système de l'interface utilisateur lisse et flux.  
  
##### Propriétés de l'animation  
  
-   Démarrage d'opacité: 0 % de fondu, 100 % pour le fondu  
  
-   Opacité de fin : 100 % pour le fondu, fondu % 0  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu'il est utilisé dans le cadre d'une séquence d'animation de combinaison  
  
-   Style d'accélération : sinus InOut  
  
##### Exemples  
  
-   Masquer les fenêtres Outil  
  
-   Menu Ouvrir et fermer  
  
-   Transitions onglet en arrière\-plan et de premier plan  
  
#### Mélange de couleurs de A à B  
 Avec ce modèle, un élément d'interface utilisateur change de couleur une par couleur b :  
  
 ![Color blend animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202\-d\_ColorBlend")  
  
##### Utilisation correcte  
 Comme une transition animée lorsqu'un élément d'interface utilisateur change de couleur à partir d'un contexte ou état vers un autre.  
  
##### Propriétés de l'animation  
  
-   Couleur de début : interface utilisateur spécifique  
  
-   Couleur de fin : l'interface utilisateur spécifique  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu'il est utilisé dans le cadre d'une séquence d'animation de combinaison  
  
-   Style d'accélération : sinus InOut  
  
##### Exemples  
  
-   Transitions d'état de fenêtre de document \(actif, la dernière actives et inactives\)  
  
-   Transitions d'état de fenêtre d'outils \(actif et inactif\)  
  
#### Développez et de contrat  
 Avec ce modèle, un élément d'interface utilisateur se développe en X, Y ou les deux sens :  
  
 ![Expand&#47;Contract animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202\-e\_ExpandContract")  
  
##### Utilisation correcte  
 Comme une transition animée lorsqu'un élément d'interface utilisateur modifie la taille d'un contexte à un autre.  
  
##### Propriétés de l'animation  
  
-   Échelle x: % ou une dimension spécifique \(en pixels\)  
  
-   Échelle Y: % ou une dimension spécifique \(en pixels\)  
  
-   Ancrer position : généralement supérieur gauche \(pour les langues de gauche à droite\) ou supérieur droit \(pour les langues de droite à gauche\)  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu'il est utilisé dans le cadre d'une séquence d'animation de combinaison  
  
##### Exemples  
  
-   Volet Explorateur d'architecture développer \/ réduire  
  
-   Élément de Page de démarrage, développer et réduire  
  
#### X\-Y placer les modifications  
 Avec ce modèle, un élément d'interface utilisateur change sa position X ou Y ou les deux :  
  
 ![X&#47;Y position change animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202\-f\_XYPositionChange")  
  
##### Utilisation correcte  
 Comme une transition animée lorsqu'un élément d'interface utilisateur modifie la position d'un contexte à un autre.  
  
##### Propriétés de l'animation  
  
-   Position de début de X et Y: interface utilisateur spécifique  
  
-   Position de fin de X et Y: interface utilisateur spécifique  
  
-   Trajectoire : aucun  
  
-   Durée : 200 millisecondes autonome, 100 millisecondes lorsqu'il est utilisé dans le cadre d'une séquence d'animation de combinaison  
  
-   Style d'accélération : sinus InOut  
  
##### Exemple  
 Réorganisation de l'onglet  
  
#### Faire pivoter  
 Avec ce modèle, l'élément d'interface utilisateur fait pivoter :  
  
 ![Rotate animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202\-g\_Rotate")  
  
##### Utilisation correcte  
 Uniquement pour l'indicateur de progression indéterminée en rotation.  
  
##### Propriétés de l'animation  
  
-   Degré de rotation : 360  
  
-   Centre de rotation : au milieu de l'objet  
  
-   Durée : continue  
  
##### Exemple  
 Indicateur de progression indéterminée \(rotation\)  
  
### Les actions de l'interface utilisateur shell courantes et les animations recommandées  
  
#### Onglet ouvert  
  
-   Style : apparaissent  
  
-   Durée : Zéro seconde  
  
 ![Tab open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202\-h\_TabOpen")  
  
#### Onglet fermer  
  
-   Style : Modification de position X  
  
-   Durée : 200 millisecondes  
  
 ![Tab close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202\-i\_TabClose")  
  
#### Onglet commande  
  
-   Style : Modification de position X  
  
-   Durée : 200 millisecondes  
  
 ![Tab reorder animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202\-j\_TabReorder")  
  
#### Fermer document flottante  
  
-   Style : apparaissent  
  
-   Durée : 200 millisecondes  
  
 ![Close floating document animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202\-k\_CloseFloatingDocument")  
  
#### Transition d'état de fenêtre  
  
-   Style : Pour être cohérent avec d'autres fenêtres, permettent de système d'exploitation définir l'animation fermer le document.  
  
-   Durée : 200 millisecondes  
  
 ![Window state transition animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202\-l\_WindowStateTransition")  
  
#### Menu Ouvrir  
  
-   Style : fondu  
  
-   Durée : 200 millisecondes  
  
 ![Menu open animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202\-m\_MenuOpen")  
  
#### Fermer le menu  
  
-   Style : fondu  
  
-   Durée : 200 millisecondes  
  
 ![Menu close animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202\-n\_MenuClose")  
  
#### Masquer automatiquement la divulgation de fenêtre outil  
  
-   Style : apparaissent  
  
-   Durée : Zéro seconde  
  
 ![Auto&#45;hide tool window animation in Visual Studio](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202\-o\_AutoHideToolWindowReveal")