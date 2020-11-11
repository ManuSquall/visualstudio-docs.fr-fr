---
title: Visual Studio pour Mac pour les utilisateurs Windows
description: Présentation de la Visual Studio pour Mac pour les développeurs connaissant l’utilisation de Visual Studio sur le système d’exploitation Windows.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: 880811c675aac34a18a65c6eccb8ee10f3347d4c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493372"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio pour Mac pour les utilisateurs Windows

La migration d’un système d’exploitation vers un autre peut être décourageante. Il existe souvent des différences subtiles entre les applications multiplateformes, de l’interface utilisateur à la catégorisation des éléments de menu. Vous découvrirez ici les différences les plus courantes entre Visual Studio pour Mac et Visual Studio pour Windows. Vous allez également découvrir quelques conventions différentes entre macOS et Windows.

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

En tant que développeurs, un grand nombre d’entre vous seront habitués à utiliser le clavier pour vos tâches et votre navigation. Certaines touches du clavier sont communes entre les Mac et les PC Windows. Vous pourriez être inversée pour penser que les actions du clavier, telles que copier et coller, utilisent les mêmes combinaisons de touches. Ce n’est pas toujours le cas. Heureusement, vous pouvez modifier vos combinaisons de touches dans Visual Studio pour Mac pour qu’elles correspondent étroitement à celles de Visual Studio dans Windows.

La première fois que vous exécutez Visual Studio pour Mac la fenêtre de sélection des raccourcis clavier s’affiche : ![ fenêtre combinaisons de touches](media/ide-tour-2019-keyboard-shortcut.png)

Si vous souhaitez modifier les combinaisons de touches ultérieurement, vous pouvez trouver le paramètre dans Préférences : combinaisons de ![ touches préférences.](media/customizing-the-ide-image10a.png)

Il est important de noter que macOS utilise différents raccourcis au niveau du système pour Windows. La modification des préférences de combinaison de touches vous permettra d’utiliser des raccourcis Windows familiers dans Visual Studio pour Mac. Toutefois, dans d’autres zones de macOS, vous devez être familiarisé avec les raccourcis macOS.

La touche de modification de commande macOS (⌘) peut généralement remplacer la clé de contrôle dans Windows. Voici quelques exemples, ainsi que d’autres raccourcis couramment utilisés :

|Tâche                   |Raccourci Windows         |Raccourci macOS      |
|-----------------------|-------------------------|--------------------|
|Copier                   |`Ctrl + C`               |`⌘ + C`             |
|Coller                  |`Ctrl + V`               |`⌘ + V`             |
|Couper                    |`Ctrl + X`               |`⌘ + X`             |
|Annuler                   |`Ctrl + Z`               |`⌘ + Z`             |
|Rétablir                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Supprimer à droite du curseur |`Delete`                 |`fn + Backspace`    |
|Supprimer le mot            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Vous trouverez une liste complète des raccourcis macOS sur le [site Web du support technique Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menus

Les menus dans macOS sont organisés différemment des menus de Windows. Visual Studio pour Mac n’est pas une exception. Vous trouverez ci-dessous quelques-unes des options de menu les plus courantes :

|Tâche                   |Visual Studio (Windows)                                              |Visual Studio pour Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Préférences (options)  |Outils > options...                                                   |Préférences de Visual Studio >...       |
|Extensions             |Extensions > gérer les extensions                                       |Extensions de > Visual Studio...        |
|Dispositions                |Fenêtre > appliquer la disposition de fenêtre > [sélectionner la disposition]                       |Afficher > disposition > [sélectionner la disposition]               |
|Mises à jour                |Aide > la vérification des mises à jour                                             |> Visual Studio Rechercher les mises à jour... |
|Gestionnaire de package NuGet  |Outils > gestionnaire de package NuGet > gérer les packages ou la solution NuGet... |Projet > gérer les packages NuGet...   |
|Rechercher des outils             |Modifier > Rechercher et remplacer des > [Select Tool]                              |> de recherche [outil Select]               |
|À propos de Visual Studio    |Aide > sur Microsoft Visual Studio                                 |Visual Studio > à propos de Visual Studio  

> [!NOTE]
> Vous trouverez une vue d’ensemble des fonctionnalités les plus courantes dans Visual Studio pour Mac dans la [visite IDE](ide-tour.md)