---
title: Guide pratique pour se déplacer dans l’IDE
description: Découvrez comment vous déplacer dans l’IDE de Visual Studio de la fenêtre à la fenêtre et du fichier au fichier de différentes façons.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 384a6252ef17709970f6e902dfdf83a157b0460a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968045"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Guide pratique pour naviguer dans l’IDE Visual Studio

L’environnement de développement intégré (IDE) a été conçu pour vous permettre de vous déplacer de fenêtre en fenêtre et de fichier en fichier de différentes façons, selon vos préférences ou exigences de projet. Vous pouvez choisir de parcourir tous les fichiers ouverts de l'éditeur ou de parcourir toutes les fenêtres Outil actives dans l'IDE. Vous pouvez aussi basculer directement vers tout fichier ouvert dans l'éditeur, indépendamment de son dernier ordre d'accès. Ces fonctionnalités peuvent contribuer à accroître votre productivité lorsque vous travaillez dans l’IDE.

> [!NOTE]
> Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans cet article, en fonction de vos paramètres actifs ou de votre édition. Cet article concerne les paramètres **Général**. Pour modifier vos paramètres, par exemple pour définir les paramètres **Général** ou **Visual C++**, choisissez **Outils** > **Importation et exportation de paramètres**, puis choisissez **Réinitialiser tous les paramètres**.

## <a name="keyboard-shortcuts"></a>Raccourcis clavier

Presque toutes les commandes de menu dans Visual Studio sont associées à un raccourci clavier. Vous pouvez également créer vos propres raccourcis personnalisés. Pour plus d’informations, consultez [Identifier et personnaliser les raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Naviguer parmi les fichiers de l’éditeur

Vous pouvez utiliser plusieurs méthodes pour parcourir les fichiers ouverts dans l'éditeur. Vous pouvez vous déplacer entre les fichiers en fonction de l'ordre dans lequel vous y accédez, utiliser le Navigateur IDE pour trouver rapidement un fichier ouvert ou encore épingler vos fichiers favoris à la zone de configuration des onglets pour qu'ils soient toujours visibles.

Les options Naviguer vers l’arrière et Naviguer vers l’avant permettent de parcourir les fichiers ouverts dans l’éditeur en fonction de l’ordre dans lequel ils ont fait l’objet d’un accès, à l’image des options Précédent et Suivant qui permettent d’afficher l’historique dans Microsoft Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Pour parcourir les documents ouverts par ordre d'utilisation

- Pour activer les documents ouverts dans l’ordre dans lequel ils ont été horodatés le plus récemment, appuyez sur **CTRL** + **-** (trait d’Union).

- Pour activer les documents ouverts dans l’ordre inverse, appuyez sur **CTRL** + **MAJ** + **-** (trait d’Union).

    > [!NOTE]
    > **Naviguer vers l’arrière** et **Naviguer vers l’avant** sont aussi disponibles dans le menu **Affichage**.

Vous pouvez également basculer vers un fichier spécifique ouvert dans l’éditeur, indépendamment de la date à laquelle vous y avez accédé pour la dernière fois, à l’aide du **Navigateur IDE**, de la liste **Fichiers actifs** de l’éditeur ou de la boîte de dialogue **Fenêtres**.

Le **Navigateur IDE** fonctionne de façon très similaire au commutateur d’applications Windows. Il n'est pas disponible à partir des menus et il n'est accessible qu'à l'aide des touches de raccourci. Vous pouvez utiliser l’une des deux commandes disponibles pour accéder au **Navigateur IDE** (illustré ci-dessous) afin de parcourir des fichiers, selon l’ordre de défilement de votre choix.

![Navigateur de l'IDE Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` vous permet de passer au fichier ayant le plus récemment fait l'objet d'un accès, tandis que `Window.NextDocumentWindowNav` vous permet de vous déplacer dans le sens contraire. Les **Paramètres de développement généraux** permettent d’affecter **Maj**+**Alt**+**F7** à `Window.PreviousDocumentWindowNav` et **Alt**+**F7** à `Window.NextDocumentWindowNav`.

> [!NOTE]
> Si la combinaison de paramètres que vous utilisez ne possède pas déjà une combinaison de touches de raccourci attribuée à cette commande, vous pouvez assigner votre propre commande personnalisée à l’aide de la page **Clavier** de la boîte de dialogue **Options**. Pour plus d’informations, consultez [Identifier et personnaliser les raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Pour basculer vers des fichiers spécifiques dans l'éditeur

- Appuyez sur **CTRL** + **Tab** pour afficher le **navigateur IDE**. Maintenez la touche **CTRL** enfoncée et appuyez sur **Tab** à plusieurs reprises jusqu’à ce que vous sélectionnez le fichier vers lequel vous souhaitez basculer.

    > [!TIP]
    > Pour inverser l’ordre dans lequel vous parcourez la liste **Fichiers actifs**, maintenez les touches **Ctrl**+**Maj** enfoncées et appuyez sur **Tab**.

    \- ou -

- Dans le coin supérieur droit de l’éditeur, choisissez le bouton **Fichiers actifs**, puis sélectionnez dans la liste un fichier vers lequel vous souhaitez basculer.

    \- ou -

- Dans la barre de menus, choisissez fenêtres de **fenêtre**  >  .

- Dans la liste, sélectionnez le fichier à afficher, puis choisissez **Activer**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Naviguer parmi les fenêtres Outil dans l’IDE

Le **Navigateur IDE** vous permet également de parcourir les fenêtres Outil que vous avez ouvertes dans l’IDE. Vous pouvez utiliser l’une des deux commandes disponibles pour accéder au **Navigateur IDE** afin de parcourir des fenêtres Outil, selon l’ordre de défilement de votre choix. `Window.PreviousToolWindowNav` vous permet de passer au fichier ayant le plus récemment fait l'objet d'un accès, tandis que `Window.NextToolWindowNav` vous permet de vous déplacer dans le sens contraire. Les **Paramètres de développement généraux** permettent d’affecter **Maj**+**Alt**+**F7** à `Window.PreviousDocumentWindowNav` et **Alt**+**F7** à `Window.NextDocumentWindowNav`.

> [!NOTE]
> Si la combinaison de paramètres que vous utilisez ne possède pas déjà une combinaison de touches de raccourci attribuée à cette commande, vous pouvez assigner votre propre commande personnalisée à l’aide de la page **Clavier** de la boîte de dialogue **Options**. Pour plus d’informations, consultez [Identifier et personnaliser les raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Pour basculer vers une fenêtre Outil spécifique dans l'IDE

- Appuyez sur **ALT** + **F7** pour afficher le **navigateur IDE**. Maintenez la touche **ALT** enfoncée et appuyez sur **F7** à plusieurs reprises jusqu’à ce que vous ayez sélectionné la fenêtre vers laquelle vous souhaitez basculer.

    > [!TIP]
    > Pour inverser l’ordre dans lequel vous parcourez la liste **Fenêtres Outil actives**, maintenez enfoncées les touches **Maj**+**Alt**, puis appuyez sur **F7**.

## <a name="see-also"></a>Voir aussi

- [Personnaliser les dispositions de fenêtres](../ide/customizing-window-layouts-in-visual-studio.md)
- [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md)
