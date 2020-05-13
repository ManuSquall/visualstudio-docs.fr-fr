---
title: Studio visuel pour Mac pour les utilisateurs de Windows
description: Introduction de fonctionnalités d’accessibilité dans Visual Studio pour Mac et comment elles peuvent être activées.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984260"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Studio visuel pour Mac pour les utilisateurs de Windows

La migration d’un système d’exploitation à l’autre peut être intimidante. Il existe souvent des différences subtiles dans les applications multiplateformes, de l’interface utilisateur à la catégorisation des éléments de menu. Les utilisateurs auront également la courbe d’apprentissage de l’acclimatation à l’interface utilisateur du nouveau système d’exploitation. Ici, vous apprendrez les différences les plus courantes entre Visual Studio pour Mac et Visual Studio pour Windows. Vous apprendrez également quelques conventions différentes entre macOS et Windows.

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

En tant que développeurs, beaucoup d’entre vous seront habitués à utiliser le clavier pour vos tâches et votre navigation. Certaines touches sur le clavier sont communes entre les Mac et les PC Windows. Vous pourriez être pardonné de penser que les actions de clavier telles que la copie et la pâte utilisent les mêmes combinaisons de clés. Ce n’est pas toujours le cas. Heureusement, vous pouvez modifier vos liaisons clés dans Visual Studio pour Mac pour correspondre étroitement à celles de Visual Studio dans Windows.

La première fois que vous exécutez Visual Studio pour Mac, ![vous verrez la fenêtre de sélection des raccourcis clavier: Fenêtre de fixations clés](media/ide-tour-2019-keyboard-shortcut.png)

Si vous souhaitez modifier les liaisons clés plus tard, vous ![pouvez trouver le paramètre dans les préférences : préférences de fixations clés](media/customizing-the-ide-image10a.png)

Il est important de noter que macOS utilise différents raccourcis à l’échelle du système pour Windows. Changer les préférences de liaison clés vous permettra d’utiliser des raccourcis Windows familiers dans Visual Studio pour Mac. Cependant, dans d’autres domaines de macOS, vous devrez être familier avec les raccourcis macOS.

La clé modificateur macOS Command () peut généralement remplacer la clé de contrôle dans Windows. Voici quelques exemples, et d’autres raccourcis couramment utilisés:

|Tâche                   |Raccourci Windows         |Raccourci macOS      |
|-----------------------|-------------------------|--------------------|
|Copier                   |`Ctrl + C`               |`⌘ + C`             |
|Coller                  |`Ctrl + V`               |`⌘ + V`             |
|Couper                    |`Ctrl + X`               |`⌘ + X`             |
|Annuler                   |`Ctrl + Z`               |`⌘ + Z`             |
|Rétablir                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Supprimer le droit du curseur |`Delete`                 |`fn + Backspace`    |
|Supprimer le mot            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Vous pouvez trouver une liste complète de raccourcis macOS sur le [site Web Apple Support](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Menus

Les menus en macOS sont organisés différemment des menus de Windows. Visual Studio pour Mac ne fait pas exception. Vous pouvez trouver quelques-unes des options de menu les plus courantes ici:

|Tâche                   |Visual Studio (Windows)                                              |Visual Studio pour Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Préférences (Options)  |Outils > Options...                                                   |Visual Studio > Préférences...       |
|Extensions             |Extensions > Gérer les extensions                                       |Visual Studio > Extensions...        |
|Mises en forme                |Fenêtre > Appliquer la mise en page des fenêtres > [Sélection de la mise en page]                       |Afficher > [Sélection de la mise en page]               |
|Mises à jour                |Aidez-> vérifier les mises à jour                                             |Visual Studio > Vérifier pour les mises à jour ... |
|Gestionnaire de package NuGet  |Outils > Gestionnaire de paquets NuGet > Gérer les forfaits Ou la solution NuGet... |Projet > Gérer les forfaits NuGet...   |
|Pads / Windows         |Voir > [Select Pad / fenêtre]                                         |Voir > Pads > [Select pad / window]  |
|Trouver des outils             |Modifier > Trouver et remplacer > [Outil de sélection]                              |Rechercher > [Outil de sélection]               |
|À propos de Visual Studio    |Aidez-> sur Microsoft Visual Studio                                 |Visual Studio > Propos Visual Studio  

> [!NOTE]
> Vous pouvez trouver un aperçu des caractéristiques les plus courantes dans Visual Studio for Mac dans [l’IDE Tour](ide-tour.md)