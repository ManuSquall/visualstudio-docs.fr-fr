---
title: 'Comment : déplacer dans l’IDE | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94629a2e64d154313711b3e8968b28959d3341e8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54805417"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Comment : se déplacer dans l'IDE de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’environnement de développement intégré (IDE) a été conçu pour vous permettre de vous déplacer de fenêtre en fenêtre et de fichier en fichier de différentes façons, selon vos préférences ou exigences de projet. Vous pouvez choisir de parcourir tous les fichiers ouverts de l'éditeur ou de parcourir toutes les fenêtres Outil actives dans l'IDE. Vous pouvez aussi basculer directement vers tout fichier ouvert dans l'éditeur, indépendamment de son dernier ordre d'accès. Ces fonctionnalités peuvent contribuer à accroître votre productivité lorsque vous travaillez dans l’IDE.

> [!NOTE]
>  Les options disponibles dans les boîtes de dialogue, ainsi que les noms et emplacements des commandes de menu que vous voyez, peuvent différer de ce qui est décrit dans l'aide selon vos paramètres actifs ou votre édition. Cette page d’aide concerne les **Paramètres de développement généraux**. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Raccourcis clavier
 Presque toutes les commandes de menu dans Visual Studio sont associées à un raccourci clavier. Vous pouvez également créer vos propres raccourcis personnalisés. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Navigation entre les fichiers dans l'éditeur
 Vous pouvez utiliser plusieurs méthodes pour parcourir les fichiers ouverts dans l'éditeur. Vous pouvez vous déplacer entre les fichiers en fonction de l'ordre dans lequel vous y accédez, utiliser le Navigateur IDE pour trouver rapidement un fichier ouvert ou encore épingler vos fichiers favoris à la zone de configuration des onglets pour qu'ils soient toujours visibles.

 Naviguer vers l'arrière et Naviguer vers l'avant permettent de parcourir les fichiers ouverts dans l'éditeur en fonction de l'ordre dans lequel ils ont fait l'objet d'un accès, à l'image de Précédent et Suivant pour afficher l'historique dans Microsoft Internet Explorer.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Pour parcourir les documents ouverts par ordre d'utilisation

- Pour activer les documents ouverts dans l'ordre dans lequel ils ont le plus récemment fait l'objet d'un accès, appuyez sur Ctrl + Signe moins (-).

- Pour activer les documents ouverts dans l'ordre inverse, appuyez sur Ctrl + Maj + Signe moins (-).

  > [!NOTE]
  >  **Naviguer vers l’arrière** et **Naviguer vers l’avant** sont aussi disponibles dans le menu **Affichage**.

  Vous pouvez également basculer vers un fichier spécifique ouvert dans l’éditeur, indépendamment de la date à laquelle vous y avez accédé pour la dernière fois, à l’aide du **Navigateur IDE**, de la liste **Fichiers actifs** de l’éditeur ou de la boîte de dialogue **Fenêtres**.

  Le **Navigateur IDE** fonctionne de façon très similaire au commutateur d’applications Windows. Il n'est pas disponible à partir des menus et il n'est accessible qu'à l'aide des touches de raccourci. Vous pouvez utiliser l’une des deux commandes disponibles pour accéder au **Navigateur IDE** (illustré ci-dessous) afin de parcourir des fichiers, selon l’ordre de défilement de votre choix.

  ![Navigateur de l’IDE Visual Studio](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` vous permet de passer au fichier ayant le plus récemment fait l'objet d'un accès, tandis que `Window.NextDocumentWindowNav` vous permet de vous déplacer dans le sens contraire. Les paramètres de développement généraux assignent Ctrl + Maj + Tab à `Window.PreviousDocumentWindowNav` et Ctrl + Tab à `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Si la combinaison de paramètres que vous utilisez ne possède pas déjà une combinaison de touches de raccourci attribuée à cette commande, vous pouvez assigner votre propre commande personnalisée à l’aide de la page **Clavier** de la boîte de dialogue **Options**. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Pour basculer vers des fichiers spécifiques dans l'éditeur

-   Appuyez sur Ctrl + Tab pour afficher le **Navigateur IDE**. Maintenez la touche Ctrl enfoncée et appuyez sur Tab à plusieurs reprises jusqu'à ce que vous sélectionniez le fichier vers lequel vous souhaitez basculer.

    > [!TIP]
    >  Pour inverser l’ordre dans lequel vous parcourez la liste **Fichiers actifs**, maintenez les touches Ctrl + Maj enfoncées et appuyez sur Tab.

     \- ou -

-   Dans le coin supérieur droit de l’éditeur, choisissez le bouton **Fichiers actifs**, puis sélectionnez dans la liste un fichier vers lequel vous souhaitez basculer.

     \- ou -

-   Dans la barre de menus, sélectionnez **Fenêtre**, **Fenêtres**.

-   Dans la liste, sélectionnez le fichier à afficher, puis choisissez **Activer**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Navigation entre les fenêtres Outil dans l'IDE
 Le **Navigateur IDE** vous permet également de parcourir les fenêtres Outil que vous avez ouvertes dans l’IDE. Vous pouvez utiliser l’une des deux commandes disponibles pour accéder au **Navigateur IDE** afin de parcourir des fenêtres Outil, selon l’ordre de défilement de votre choix. `Window.PreviousToolWindowNav` vous permet de passer au fichier ayant le plus récemment fait l'objet d'un accès, tandis que `Window.NextToolWindowNav` vous permet de vous déplacer dans le sens contraire. Les paramètres de développement généraux assignent Maj + Alt + F7 à `Window.PreviousDocumentWindowNav` et Alt + F7 à `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Si la combinaison de paramètres que vous utilisez ne possède pas déjà une combinaison de touches de raccourci attribuée à cette commande, vous pouvez assigner votre propre commande personnalisée à l’aide de la page **Clavier** de la boîte de dialogue **Options**. Pour plus d’informations, consultez [Identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Pour basculer vers une fenêtre Outil spécifique dans l'IDE

-   Appuyez sur Alt + F7 pour afficher le **Navigateur IDE**. Maintenez la touche Alt enfoncée et appuyez sur F7 à plusieurs reprises jusqu'à ce que vous sélectionniez la fenêtre vers laquelle vous souhaitez basculer.

    > [!TIP]
    >  Pour inverser l’ordre dans lequel vous parcourez la liste **Fenêtres Outil actives**, maintenez les touches Maj + Alt enfoncées et appuyez sur F7.

## <a name="see-also"></a>Voir aussi
 [Personnalisation des dispositions de fenêtre](../ide/customizing-window-layouts-in-visual-studio.md) [raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md)
