---
title: Visite guidée de la fonctionnalité Blend pour Visual Studio
titleSuffix: ''
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58b2e84a28a2d453eb109915bb9c38672b6bed98
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484119"
---
# <a name="blend-for-visual-studio-overview"></a>Vue d’ensemble de Blend for Visual Studio

Blend pour Visual Studio vous aide à concevoir des applications web et Windows basées sur XAML. Il fournit la même expérience de conception XAML de base que Visual Studio et ajoute des concepteurs visuels pour des tâches avancées telles que les animations et les comportements. Pour obtenir une comparaison entre Blend et Visual Studio, consultez [Conception XAML dans Visual Studio et Blend pour Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend pour Visual Studio est un composant de Visual Studio. Pour installer Blend, dans le **programme d’installation de Visual Studio**, choisissez la charge de travail **Développement de la plateforme universelle Windows** ou **Développement .NET Desktop**. Ces deux charges de travail incluent le composant Blend pour Visual Studio.

![Composants de la charge de travail UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Composants de la charge de travail Développement .NET Desktop](media/installer-dotnet-desktop.png)

Si vous débutez avec Blend pour Visual Studio, prenez un moment pour vous familiariser avec les fonctionnalités uniques de l’espace de travail. Cette rubrique vous en livre une présentation rapide.

> [!NOTE]
> Pour parcourir les fonctionnalités de conception partagées telles que la planche graphique, la fenêtre **Structure du document** et la fenêtre **Périphérique**, consultez [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="tour-of-the-tools-panel"></a>Présentation du panneau Outils

Vous pouvez utiliser le panneau **Outils** dans Blend pour Visual Studio pour créer et modifier les objets de votre application. Vous créez les objets en sélectionnant un outil, puis en dessinant sur la planche graphique à l'aide de la souris.

![Volet Outils](../designers/media/blend5toolspanel.png)

|||||
|-|-|-|-|
|![Outils de sélection](../designers/media/b1_1.png)|**Outils de sélection** Permet de sélectionner les objets et les tracés.<br /><br /> L’outil **Sélection directe** permet de sélectionner les objets imbriqués et les segments de tracé.|![Légende A](../designers/media/b5_label_a.png)|**Outils Dégradé et Pinceau**|
|![Outils d’affichage](../designers/media/b1_2.png)|**Outils d’affichage** Permet d’ajuster la vue de la planche graphique, par exemple pour l’affichage panoramique et le zoom.|![Légende B](../designers/media/b5_label_b.png)|**Outils de tracé**|
|![Outils Pinceau](../designers/media/b1_3.png)|**Outils Pinceau** Permet de manipuler les attributs visuels d’un objet, notamment de transformer un pinceau, peindre un objet ou sélectionner les attributs d’un objet pour les appliquer à un autre.|![Légende C](../designers/media/b5_label_c.png)|**Outils Forme**|
|![Outils d’objet](../designers/media/b1_4.png)|**Outils d’objet** Permet de dessiner les objets les plus courants sur la planche graphique, tels que les tracés, les formes, les panneaux de disposition, le texte et les contrôles.|![Légende D](../designers/media/b5_label_d.png)|**Panneaux de disposition**|
|![Outils de composant](../designers/media/b1_5.png)|**Outils de composant** Donne accès au panneau **Composants** et affiche le dernier composant utilisé de la bibliothèque.|![Légende E](../designers/media/b5_label_e.png)|**Contrôles de texte**|
|||![Légende F](../designers/media/b5_label_f.png)|**Contrôles courants**|

**Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [La barre d’outils](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4).

## <a name="tour-of-the-assets-panel"></a>Présentation du panneau Composants

Tous les contrôles se trouvent dans le panneau **Composants**, à l’image de la **boîte à outils** de Visual Studio. Outre les contrôles, vous y trouverez tout ce que vous pouvez ajouter à la planche graphique dans le panneau **Composants**, notamment des styles, des médias, des comportements et des effets.

![Volet Composants](../designers/media/blend5_assets_panel.png)

|||
|-|-|
|![](../designers/media/b1_1.png)|**Zone de recherche** Tapez un élément dans la zone **Rechercher** pour filtrer la liste des composants.|
|![Mode Grille et mode Liste](../designers/media/b1_2.png)|**Mode Grille et mode Liste** Passez du **mode Grille** au **mode Liste**, et inversement, dans l’affichage des composants.|
|![Catégories Composants](../designers/media/b1_3.png)|**Catégories Composants** Cliquez sur une catégorie ou une sous-catégorie pour afficher la liste des composants dans cette catégorie.|
|![Styles](../designers/media/b1_4.png)|**Styles** Affiche tous les styles contenus dans le dictionnaire de ressources.|
|![Description](../designers/media/b1_5.png)|**Description** Affiche une description de la catégorie ou sous-catégorie de composants sélectionnée.|

## <a name="tour-of-the-objects-and-timeline-panel"></a>Présentation du panneau Objets et chronologie

Ce panneau permet de disposer les objets sur la planche graphique et éventuellement de les animer.

![Volet Objets et chronologie en mode animation](../designers/media/b5_object_timeline_animation.png)

|||
|-|-|
|![Liste d’objets](../designers/media/b1_1.png)|**Liste d’objets** Affiche une arborescence visuelle d’un document. Vous pouvez explorer divers niveaux de détail. Vous pouvez aussi ajouter des couches pour mieux disposer les objets sur la planche graphique. Vous pouvez ainsi les verrouiller et les masquer en groupe.|
|![Indicateur du mode d’enregistrement](../designers/media/b1_2.png)|**Indicateur du mode d’enregistrement** Indique si vous enregistrez les modifications apportées aux propriétés dans une chronologie.|
|![Sélecteur de tables de montage séquentiel](../designers/media/b1_3.png)|**Sélecteur de tables de montage séquentiel** Affiche la liste des tables de montage séquentiel que vous avez créées.|
|![Fermer la table de montage séquentiel](../designers/media/b1_4.png)|**Fermer la table de montage séquentiel** Ferme la table de montage séquentiel active.|
|![Options de table de montage séquentiel](../designers/media/b1_5.png)|**Options de table de montage séquentiel** Permet de créer, dupliquer, inverser, supprimer, renommer ou fermer une table de montage séquentiel.|
|![Contrôles de lecture](../designers/media/b1_6.png)|**Contrôles de lecture** Permet de parcourir la chronologie. Vous pouvez également faire glisser la tête de lecture pour naviguer (ou *lire à vitesse variable*) dans la chronologie.|
|![Rétablir l’étendue à](../designers/media/b1_7.png)|**Rétablir l’étendue à** Permet de rétablir l’objet racine précédent ou l’étendue précédente de la liste d’objets. Cela n’est possible qu’à l’occasion de la modification d’un style ou d’un modèle.|
|![Enregistrer une image clé](../designers/media/b1_8.png)|**Enregistrer une image clé** Permet d’enregistrer une capture instantanée des propriétés de l’objet sélectionné au moment dans le temps actuel.|
|![Options d’alignement](../designers/media/b1_9.png)|**Options d’alignement** Permet de définir l’alignement de la chronologie, la résolution d’alignement, et de désactiver l’alignement de la chronologie.|
|![Afficher ou masquer Verrouiller/déverrouiller](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Afficher/masquer**, **Verrouiller/déverrouiller** Permet d’afficher ou de masquer les options de visibilité et de verrouillage de la liste d’objets.|
|![Position de la tête de lecture dans la chronologie](../designers/media/b1_11.png)|**Position de la tête de lecture dans la chronologie** Affiche le temps actuel en millisecondes. Il est également possible d’entrer une valeur de temps directement dans ce champ pour atteindre un instant particulier. La précision dépend de la résolution d’alignement définie dans **Options d’alignement**.|
|![Tête de lecture](../designers/media/b1_12.png)|**Tête de lecture** Indique à quel point dans le temps se situe l’animation. Vous pouvez faire glisser la tête de lecture sur la chronologie pour afficher un aperçu de l'animation.|
|![Images clés définies sur les chronologies](../designers/media/b1_13.png)|**Images clés définies sur les chronologies** Permet de modifier une valeur de propriété à un moment précis dans le temps.|
|![Modifier l’ordre des objets](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Modifier l’ordre des objets** Permet de définir l’ordre d’affichage des objets. Cliquez sur ce bouton pour organiser les objets dans la vue de structure selon l’ordre de plan (de l’avant vers l’arrière) ou l’ordre des balises (ordre dans lequel elles sont affichées dans la vue **XAML**).|
|![Zoom de la chronologie](../designers/media/b1_15.png)|**Zoom de la chronologie** Permet de définir la résolution du zoom de la chronologie. Un zoom avant permet de modifier une animation avec plus de détails, alors qu'un zoom arrière donne un plus large aperçu de ce qu'il se passe sur une période plus longue. Si vous faites un zoom avant, mais que vous ne pouvez pas définir d’image clé à un moment précis dans le temps, vérifiez que la résolution d’alignement définie est suffisamment élevée.|
|![Légende 16](../designers/media/b5_label_16.png)|**Zone de composition de la chronologie** Permet d’afficher la chronologie et de déplacer des images clés en les faisant glisser ou via leurs menus contextuels.|

## <a name="tour-of-the-properties-panel"></a>Présentation du panneau Propriétés

Cet panneau permet d'afficher et de modifier les propriétés d'un objet. Vous pouvez aussi les définir directement sur la planche graphique. Dans ce cas, les modifications apportées aux propriétés sont répercutées dans le panneau **Propriétés**.

![Panneau Propriétés](../designers/media/blend5_properties_panel.png)

**Catégories** Permet de développer et de réduire les catégories de propriétés. Cliquez sur **Développer** ![Développer](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png) et **Réduire** ![Réduire](../designers/media/b5_collapse_button.png) pour afficher ou masquer les détails de catégorie.

|||
|-|-|
|![Nom et Type](../designers/media/b1_1.png)|**Nom et Type** Affiche l’icône, le nom et le type de l’objet sélectionné.|
|![Réorganiser par](../designers/media/b1_2.png)|**Réorganiser par** Permet d’organiser les propriétés par ordre alphabétique par nom, source ou catégorie.|
|![Propriétés de pinceau](../designers/media/b1_3.png)|**Propriétés de pinceau** Permet de définir les propriétés visuelles des pinceaux, tels que les pinceaux Remplissage, Trait et Premier plan.|
|![Éditeur de couleur](../designers/media/b1_4.png)|**Éditeur de couleurs** Utilisez cette option pour les pinceaux de dégradé et de couleur unie.|
|![Sélecteur de couleurs](../designers/media/b1_5.png)|**Sélecteur de couleurs** Permet de sélectionner une couleur.|
|![Échantillons de couleur](../designers/media/b1_6.png)|**Échantillons de couleur** Présentent la couleur initiale, la couleur active et la dernière couleur.|
|![Compte-gouttes](../designers/media/b1_7.png)|**Compte-gouttes** Permet d’utiliser la couleur de tout élément sur l’écran. La **Pipette de couleur** est disponible quand le **Pinceau couleur unie** est sélectionné. La **Pipette de dégradé** est disponible lorsque le **Pinceau de dégradé** est sélectionné.|
|![Propriétés et événements](../designers/media/b1_8.png)|**Propriétés et événements** Permet de définir les propriétés ou de choisir des événements pour un élément sélectionné.|
|![Zone de recherche](../designers/media/b1_9.png)|**Zone de recherche** Permet de rechercher des propriétés. Filtrez les propriétés affichées en complétant la zone **Rechercher**.|
|![Onglets Éditeur de pinceau](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png)|**Onglets Éditeur de pinceau** Utilisez cette option pour sélectionner un éditeur de pinceau. Vous pouvez choisir **Aucun pinceau**, **Pinceau couleur unie**, **Pinceau de dégradé**, **Pinceau mosaïque** ou **Ressource pinceau**.|
|![Ressources de couleur](../designers/media/b1_11.png)|**Ressources de couleur** Permet d’appliquer exactement la même couleur à différentes propriétés. L’onglet **Ressources de couleur** inclut les **ressources locales** et les **ressources système**.|
|![Espace de couleurs RVB](../designers/media/b1_12.png)|**Espace de couleurs RVB** Permet de modifier la couleur en ajustant les valeurs des éditeurs de nombres **R**, **V** ou **B** (rouge, vert, bleu).|
|![Canal alpha](../designers/media/b1_13.png)|**Canal alpha** Modifiez la valeur alpha à l’aide de l’éditeur de nombres en regard de **A**.|
|![Convertir la couleur en ressource](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png)|**Convertir la couleur en ressource** Permet de convertir la couleur sélectionnée en ressource de couleur. Les ressources de couleur sont disponibles quand vous cliquez sur l'onglet Ressources de couleur.|
|![](../designers/media/b1_15.png)|**Valeur hexadécimale** Affiche la valeur hexadécimale de la couleur affichée.|
|![Légende 16](../designers/media/b5_label_16.png)|**Curseur de dégradé** S’affiche uniquement si un pinceau de dégradé est sélectionné.|
|![Afficher les propriétés avancées](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png)|**Afficher les propriétés avancées** Affiche les catégories de propriétés moins fréquemment utilisées.|

**Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png) [La barre d’outils](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7).

## <a name="see-also"></a>Voir aussi

- [Insérer des contrôles et modifier leur comportement](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)
- [Animer des objets](../designers/animate-objects-in-xaml-designer.md)
- [Dessiner des formes et des tracés](../designers/draw-shapes-and-paths.md)
- [Conception XAML dans Visual Studio et Blend pour Visual Studio](../designers/designing-xaml-in-visual-studio.md)
