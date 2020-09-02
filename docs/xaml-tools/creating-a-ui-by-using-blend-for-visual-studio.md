---
title: Visite guidée de la fonctionnalité Blend pour Visual Studio
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8348ba38849b76a745a56f941850d6b61a8f433f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332093"
---
# <a name="blend-for-visual-studio-overview"></a>Vue d’ensemble de Blend for Visual Studio

Blend pour Visual Studio vous aide à concevoir des applications web et Windows basées sur XAML. Il fournit la même expérience de conception XAML de base que Visual Studio et ajoute des concepteurs visuels pour des tâches avancées telles que les animations et les comportements. Pour obtenir une comparaison entre Blend et Visual Studio, consultez [Conception XAML dans Visual Studio et Blend pour Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend pour Visual Studio est un composant de Visual Studio. Pour installer Blend, dans le **programme d’installation de Visual Studio**, choisissez la charge de travail **Développement de la plateforme universelle Windows** ou **Développement .NET Desktop**. Ces deux charges de travail incluent le composant Blend pour Visual Studio.

![Composants de la charge de travail UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Composants de la charge de travail Développement .NET Desktop](media/installer-dotnet-desktop.png)

Si vous débutez avec Blend pour Visual Studio, prenez un moment pour vous familiariser avec les fonctionnalités uniques de l’espace de travail. Cette rubrique vous en livre une présentation rapide.

## <a name="tools-panel"></a>Panneau Outils

Vous pouvez utiliser le panneau **Outils** dans Blend pour Visual Studio pour créer et modifier les objets de votre application. Le panneau **Outils** s’affiche sur le côté gauche du concepteur XAML quand un fichier *.xaml* est ouvert.

Vous créez les objets en sélectionnant un outil, puis en dessinant sur la planche graphique à l'aide de la souris.

![Panneau Outils dans Blend pour Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Certains des outils du panneau **Outils** comprennent des variations. Par exemple, ils vous permettent de choisir une ellipse ou une ligne au lieu d’un rectangle. Pour accéder à ces variantes, cliquez avec le bouton droit sur l’outil ou cliquez dessus en maintenant le bouton de la souris enfoncé.
>
> ![Variantes de l’outil Forme dans Blend pour Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Outils de sélection

Sélectionnez des objets et des tracés. L’outil **Sélection directe** permet de sélectionner les objets imbriqués et les segments de tracé.

### <a name="view-tools"></a>Outils d’affichage

Ajustez la vue de la planche graphique, par exemple, pour obtenir un affichage panoramique et effectuer un zoom.

### <a name="brush-tools"></a>Outils Pinceau

Utilisez les attributs visuels d’un objet, tels que la transformation d’un pinceau ou l’application d’un dégradé.

### <a name="object-tools"></a>Outils d’objet

Dessinez les objets les plus courants sur la planche graphique, tels que les tracés, les formes, les panneaux de disposition, le texte et les contrôles.

### <a name="asset-tools"></a>Outils de composant

Accédez au panneau Composants pour voir le dernier composant utilisé de la bibliothèque.

## <a name="assets-window"></a>Fenêtre Composants

La fenêtre **Composants** contient tous les contrôles disponibles. Elle est similaire à la **boîte à outils** dans Visual Studio. En plus des contrôles, vous trouverez tout ce que vous pouvez ajouter à la planche graphique dans la fenêtre **Composants**, notamment des styles, des médias, des comportements et des effets. Pour ouvrir la fenêtre **Composants**, choisissez **Affichage** > **Fenêtre Composants** ou appuyez sur **Ctrl**+**Alt**+**X**.

![Fenêtre Composants dans Blend pour Visual Studio](media/blend-assets-window.png)

- entrez du texte dans la zone **Rechercher parmi les composants** pour filtrer la liste des composants.
- Pour les composants, basculez entre le mode Grille et le mode Liste à l’aide des boutons situés en haut à droite.

## <a name="objects-and-timeline-window"></a>Fenêtre Objets et chronologie

Utilisez cette fenêtre pour organiser les objets sur la planche graphique et éventuellement les animer. Pour ouvrir la fenêtre **Objets et chronologie**, choisissez **Afficher** > **Structure du document**. En plus des fonctionnalités fournies dans la [fenêtre Structure du document](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) de Visual Studio, la fenêtre Objets et chronologie de Blend pour Visual Studio comprend une zone de création de la chronologie sur la droite. Utilisez la chronologie lorsque vous créez et modifiez des animations.

![Fenêtre Objets et chronologie en mode animation](media/storyboard-timeline.png)

Utiliser les boutons relatifs au plan conceptuel ![Boutons du plan conceptuel dans Blend pour Visual Studio](media/storyboard-buttons.png) Pour créer, supprimer, fermer ou sélectionner un plan conceptuel. Utilisez la zone de création de la chronologie située sur la droite pour afficher la chronologie et déplacer les images clés.

Pointez sur chaque bouton de la fenêtre pour en savoir plus sur les fonctionnalités disponibles.

## <a name="see-also"></a>Voir aussi

- [Animer des objets](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Dessiner des formes et des tracés](../xaml-tools/draw-shapes-and-paths.md)
- [Conception XAML dans Visual Studio et Blend pour Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md)
