---
title: Affichage de Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fef652cbaa83fde61f098fb8fcef9558473fe19a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689549"
---
# <a name="windows-view"></a>Vue Fenêtres
Lorsque vous ouvrez Spy ++, Windows affiche une arborescence de toutes les fenêtres et les contrôles dans le système. Le nom de handle et de la classe de fenêtre sont affichés. La fenêtre du bureau actuelle est en haut de l’arborescence. Toutes les autres fenêtres sont des enfants du bureau et sont répertoriés en fonction de la hiérarchie de fenêtre standard. Fenêtres sœurs s’affichent dans les listes extensible mis en retrait sous leurs parents.

 La figure ci-dessous montre une vue de Spy ++ Windows classique avec le nœud supérieur est développé.

 ![Spy&#43; &#43; Windows vue](../debugger/media/spy--_windowsview.png "Spy ++ _WindowsView") vue Windows Spy ++

 La fenêtre du bureau actuelle est en haut de l’arborescence. Toutes les autres fenêtres sont des enfants du bureau et sont répertoriés en fonction de la hiérarchie de la fenêtre standard, avec les fenêtres sœurs classés par ordre de plan. Vous pouvez développer ou réduire un nœud parent de l’arborescence en cliquant sur le + ou - le symbole en regard du nœud.

 Lorsque la vue de Windows a le focus, vous pouvez utiliser l’outil de recherche dans les [boîte de dialogue de recherche de fenêtre](../debugger/window-search-dialog-box.md) pour afficher des informations à partir de n’importe quelle fenêtre ouverte sur votre système.

## <a name="in-this-section"></a>Dans cette section
 [Comment : utiliser l’outil recherche](../debugger/how-to-use-the-finder-tool.md) montre comment cet outil analyse windows pour les propriétés ou les messages.

 [Comment : rechercher une fenêtre dans la vue de Windows](../debugger/how-to-search-for-a-window-in-windows-view.md) explique comment rechercher une fenêtre spécifique dans la vue de Windows.

 [Comment : propriétés de la fenêtre Affichage](../debugger/how-to-display-window-properties.md) m procédures pour ouvrir la boîte de dialogue Propriétés de la fenêtre.

## <a name="related-sections"></a>Rubriques connexes
 [Vues Spy ++](../debugger/spy-increment-views.md) explique les arborescences Spy ++ de windows, les messages, les processus et les threads.

 [À l’aide de Spy ++](../debugger/using-spy-increment.md) présente l’outil Spy ++ et explique comment il peut être utilisé.

 [Boîte de dialogue de fenêtre Rechercher](../debugger/find-window-dialog-box.md) permet d’afficher les propriétés ou les messages à partir d’une fenêtre spécifique.

 [Boîte de dialogue de recherche de fenêtre](../debugger/window-search-dialog-box.md) utilisé pour rechercher le nœud pour une fenêtre spécifique dans la vue de Windows.

 [Boîte de dialogue Propriétés de fenêtre](../debugger/window-properties-dialog-box.md) utilisé pour afficher les propriétés d’une fenêtre sélectionné dans la vue de Windows.

 [Référence Spy ++](../debugger/spy-increment-reference.md) comprend les sections décrivant chaque Spy ++ menu et boîte de dialogue.