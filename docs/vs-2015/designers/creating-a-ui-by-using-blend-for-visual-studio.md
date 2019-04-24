---
title: Création d'une interface utilisateur à l'aide de Blend
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8fe6377de1be51ac0fc48904687b60ed8bbc95b1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082956"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Création d'une interface utilisateur à l'aide de Blend pour Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Blend pour Visual Studio vous aide à concevoir des applications de bureau Windows, web, [Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx) et du [Windows Store](http://msdn.microsoft.com/library/windows/apps/jj129478.aspx) basées sur XAML. Il fournit la même expérience de conception XAML de base que Visual Studio et ajoute des concepteurs visuels pour des tâches avancées telles que les animations et les comportements.

 Comme Blend pour Visual Studio est inclus dans le cadre de Visual Studio, il est inutile de le télécharger. Toutefois, vous devez le sélectionner dans le programme d’installation de Visual Studio pour l’installer sur votre système.

 Si vous débutez avec Blend pour Visual Studio, prenez un moment pour vous familiariser avec les fonctionnalités uniques de l’espace de travail. Cette rubrique vous en livre une présentation rapide.

> [!NOTE]
>  Pour parcourir les fonctionnalités de conception partagées telles que la planche graphique, la fenêtre Structure du document et la fenêtre Périphérique, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **Dans cette rubrique** :

- [Présentation du panneau Outils](#Tools)

- [Présentation du panneau Composants](#Assets)

- [Présentation du panneau Objets et chronologie](#Objects)

- [Présentation du panneau Propriétés](#Properties)

## <a name="Tools"></a> Présentation du panneau Outils
 Vous pouvez utiliser le panneau **Outils** dans Blend pour Visual Studio pour créer et modifier les objets de votre application. Vous créez les objets en sélectionnant un outil, puis en dessinant sur la planche graphique à l'aide de la souris.

 ![Panneau Outils](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|||||
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Outils de sélection** Permet de sélectionner les objets et les tracés.<br /><br /> L’outil **Sélection directe** permet de sélectionner les objets imbriqués et les segments de tracé.|![Légende A](../designers/media/b5-label-a.png "b5_label_A")|**Outils Dégradé et Pinceau**|
|![](../designers/media/b1-2.png "B1_2")|**Outils d’affichage** Permet d’ajuster la vue de la planche graphique, par exemple pour l’affichage panoramique et le zoom.|![Légende B](../designers/media/b5-label-b.png "b5_label_B")|**Outils de tracé**|
|![](../designers/media/b1-3.png "B1_3")|**Outils Pinceau** Permet de manipuler les attributs visuels d’un objet, notamment de transformer un pinceau, peindre un objet ou sélectionner les attributs d’un objet pour les appliquer à un autre.|![Légende C](../designers/media/b5-label-c.png "b5_label_C")|**Outils Forme**|
|![](../designers/media/b1-4.png "B1_4")|**Outils d’objet** Permet de dessiner les objets les plus courants sur la planche graphique, tels que les tracés, les formes, les panneaux de disposition, le texte et les contrôles.|![Légende D](../designers/media/b5-label-d.png "b5_label_D")|**Panneaux de disposition**|
|![](../designers/media/b1-5.png "B1_5")|**Outils de composant** Donne accès au panneau **Composants** et affiche le dernier composant utilisé de la bibliothèque.|![Légende E](../designers/media/b5-label-e.png "b5_label_E")|**Contrôles de texte**|
|||![Légende F](../designers/media/b5-label-f.png "b5_label_F")|**Contrôles courants**|

 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [la barre d’outils](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="Assets"></a> Présentation du panneau Composants
 Tous les contrôles se trouvent dans le panneau **Composants**, à l’image de la **boîte à outils** de Visual Studio. Outre les contrôles, vous y trouverez tout ce que vous pouvez ajouter à la planche graphique dans le panneau **Composants**, notamment des styles, des médias, des comportements et des effets.

 ![Panneau Composants](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Zone de recherche** Tapez un élément dans la zone **Rechercher** pour filtrer la liste des composants.|
|![](../designers/media/b1-2.png "B1_2")|**Mode Grille et mode Liste** Passez du **mode Grille** au **mode Liste**, et inversement, dans l’affichage des composants.|
|![](../designers/media/b1-3.png "B1_3")|**Catégories Composants** Cliquez sur une catégorie ou une sous-catégorie pour afficher la liste des composants dans cette catégorie.|
|![](../designers/media/b1-4.png "B1_4")|**Styles** Affiche tous les styles contenus dans le dictionnaire de ressources.|
|![](../designers/media/b1-5.png "B1_5")|**Description** Affiche une description de la catégorie ou sous-catégorie de composants sélectionnée.|

## <a name="Objects"></a> Présentation du panneau Objets et chronologie
 Ce panneau permet de disposer les objets sur la planche graphique et éventuellement de les animer.

 ![Panneau Objets et chronologie en mode animation](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Liste d’objets** Affiche une arborescence visuelle d’un document. Vous pouvez explorer divers niveaux de détail. Vous pouvez aussi ajouter des couches pour mieux disposer les objets sur la planche graphique. Vous pouvez ainsi les verrouiller et les masquer en groupe.|
|![](../designers/media/b1-2.png "B1_2")|**Indicateur du mode d’enregistrement** Indique si vous enregistrez les modifications apportées aux propriétés dans une chronologie.|
|![](../designers/media/b1-3.png "B1_3")|**Sélecteur de tables de montage séquentiel** Affiche la liste des tables de montage séquentiel que vous avez créées.|
|![](../designers/media/b1-4.png "B1_4")|**Fermer la table de montage séquentiel** Ferme la table de montage séquentiel active.|
|![](../designers/media/b1-5.png "B1_5")|**Options de table de montage séquentiel** Permet de créer, dupliquer, inverser, supprimer, renommer ou fermer une table de montage séquentiel.|
|![](../designers/media/b1-6.png "B1_6")|**Contrôles de lecture** Permet de parcourir la chronologie. Vous pouvez également faire glisser la tête de lecture pour naviguer (ou *lire à vitesse variable*) dans la chronologie.|
|![](../designers/media/b1-7.png "B1_7")|**Rétablir l’étendue à** Permet de rétablir l’objet racine précédent ou l’étendue précédente de la liste d’objets. Cela n'est possible qu'à l'occasion de la modification d'un style ou d'un modèle.|
|![](../designers/media/b1-8.png "B1_8")|**Enregistrer une image clé** Permet d’enregistrer une capture instantanée des propriétés de l’objet sélectionné au moment dans le temps actuel.|
|![](../designers/media/b1-9.png "B1_9")|**Options d’alignement** Permet de définir l’alignement de la chronologie, la résolution d’alignement, et de désactiver l’alignement de la chronologie.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Afficher/masquer**, **Verrouiller/déverrouiller** Permet d’afficher ou de masquer les options de visibilité et de verrouillage de la liste d’objets.|
|![](../designers/media/b1-11.png "B1_11")|**Position de la tête de lecture dans la chronologie** Affiche le temps actuel en millisecondes. Il est également possible d’entrer une valeur de temps directement dans ce champ pour atteindre un instant particulier. La précision dépend de la résolution d’alignement définie dans **Options d’alignement**.|
|![](../designers/media/b1-12.png "B1_12")|**Tête de lecture** Indique à quel point dans le temps se situe l’animation. Vous pouvez faire glisser la tête de lecture sur la chronologie pour afficher un aperçu de l'animation.|
|![](../designers/media/b1-13.png "B1_13")|**Images clés définies sur les chronologies** Permet de modifier une valeur de propriété à un moment précis dans le temps.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Modifier l’ordre des objets** Permet de définir l’ordre d’affichage des objets. Cliquez sur ce bouton pour organiser les objets dans la vue de structure selon l’ordre de plan (de l’avant vers l’arrière) ou l’ordre des balises (ordre dans lequel elles sont affichées dans la vue **XAML**).|
|![](../designers/media/b1-15.png "B1_15")|**Zoom de la chronologie** Permet de définir la résolution du zoom de la chronologie. Un zoom avant permet de modifier une animation avec plus de détails, alors qu'un zoom arrière donne un plus large aperçu de ce qu'il se passe sur une période plus longue. Si vous faites un zoom avant, mais que vous ne pouvez pas définir d’image clé à un moment précis dans le temps, vérifiez que la résolution d’alignement définie est suffisamment élevée.|
|![Légende 16](../designers/media/b5-label-16.png "b5_label_16")|**Zone de composition de la chronologie** Permet d’afficher la chronologie et de déplacer des images clés en les faisant glisser ou via leurs menus contextuels.|

## <a name="Properties"></a> Présentation du panneau Propriétés
 Cet panneau permet d'afficher et de modifier les propriétés d'un objet. Vous pouvez aussi les définir directement sur la planche graphique. Dans ce cas, les modifications apportées aux propriétés sont répercutées dans le panneau **Propriétés**.

 ![Panneau Propriétés](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Catégories** Permet de développer et de réduire les catégories de propriétés. Cliquez sur **Développer** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074c-421a-bbb3-6f5055b67b64") et **Réduire** ![Réduire](../designers/media/b5-collapse-button.png "b5_collapse_button") pour afficher ou masquer les détails de catégorie.

|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Nom et Type** Affiche l’icône, le nom et le type de l’objet sélectionné.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Réorganiser par** Permet d’organiser les propriétés par ordre alphabétique par nom, source ou catégorie.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Propriétés de pinceau** Permet de définir les propriétés visuelles des pinceaux, tels que les pinceaux Remplissage, Trait et Premier plan.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Éditeur de couleurs** Utilisez cette option pour les pinceaux de dégradé et de couleur unie.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Sélecteur de couleurs** Permet de sélectionner une couleur.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Échantillons de couleur** Présentent la couleur initiale, la couleur active et la dernière couleur.                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Compte-gouttes** Permet d’utiliser la couleur de tout élément sur l’écran. La **Pipette de couleur** est disponible quand le **Pinceau couleur unie** est sélectionné. La **Pipette de dégradé** est disponible lorsque le **Pinceau de dégradé** est sélectionné. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Propriétés et événements** Permet de définir les propriétés ou de choisir des événements pour un élément sélectionné.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Zone de recherche** Permet de rechercher des propriétés. Filtrez les propriétés affichées en complétant la zone **Rechercher**.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Onglets Éditeur de pinceau** Utilisez cette option pour sélectionner un éditeur de pinceau. Vous pouvez choisir **Aucun pinceau**, **Pinceau couleur unie**, **Pinceau de dégradé**, **Pinceau mosaïque** ou **Ressource pinceau**.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Ressources de couleur** Permet d’appliquer exactement la même couleur à différentes propriétés. L’onglet **Ressources de couleur** inclut les **ressources locales** et les **ressources système**.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **Espace de couleurs RVB** Permet de modifier la couleur en ajustant les valeurs des éditeurs de nombres **R**, **V** ou **B** (rouge, vert, bleu).                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Canal alpha** Modifiez la valeur alpha à l’aide de l’éditeur de nombres en regard de **A**.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Convertir la couleur en ressource** Permet de convertir la couleur sélectionnée en ressource de couleur. Les ressources de couleur sont disponibles quand vous cliquez sur l'onglet Ressources de couleur.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Valeur hexadécimale** Affiche la valeur hexadécimale de la couleur affichée.                                                                                 |
|                     ![Légende 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Curseur de dégradé** S’affiche uniquement si un pinceau de dégradé est sélectionné.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Afficher les propriétés avancées** Affiche les catégories de propriétés moins fréquemment utilisées.                                                                      |

 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [panneau Propriétés](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Voir aussi
 [Insérer des contrôles et modifier leur comportement](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [animer des objets](../designers/animate-objects-in-xaml-designer.md) [dessiner des formes et des tracés](../designers/draw-shapes-and-paths.md) [XAML de conception dans Visual Studio et Blend pour Visual Studio](../designers/designing-xaml-in-visual-studio.md)
