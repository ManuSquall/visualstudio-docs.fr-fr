---
title: Boîte de dialogue Propriétés du message | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f590f40e4e3361f4dbeb46a3a9b8758b8ab5075
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705370"
---
# <a name="message-properties-dialog-box"></a>Boîte de dialogue Propriétés du message
Utilisez cette boîte de dialogue pour en savoir plus sur un message spécifique. Pour afficher cette boîte de dialogue, déplacez le focus à un [vue Messages](../debugger/messages-view.md) fenêtre. Sélectionnez n’importe quel nœud de message dans l’arborescence, puis choisissez **propriétés** à partir de la **vue** menu.

 Le **général** onglet est le seul onglet affiché. Les paramètres suivants sont disponibles :

 **Handle de fenêtre** l’ID unique de cette fenêtre. Les numéros de handle de fenêtre sont réutilisés ; ils identifient une fenêtre uniquement pour la durée de vie de cette fenêtre. Cliquez sur cette valeur pour afficher les propriétés de cette fenêtre.

 **Niveau d’imbrication** profondeur d’imbrication de ce message, où 0 est sans imbrication.

 **Message** nombre, état et le nom du message windows sélectionné.

 **lResult** la valeur de la *lResult* paramètre, le cas échéant.

 **wParam** la valeur de la *wParam* paramètre, le cas échéant.

 **lParam** la valeur de la *lParam* paramètre, le cas échéant. Cette valeur est décodée s’il s’agit d’un pointeur vers une chaîne ou une structure.

## <a name="related-sections"></a>Rubriques connexes
 [Boîte de dialogue Options du message](../debugger/message-options-dialog-box.md) permet de sélectionner les messages sont répertoriés dans la vue Messages active.

 [Boîte de dialogue de recherche du message](../debugger/message-search-dialog-box.md) utilisé pour rechercher le nœud pour un message spécifique dans la vue Messages.

 [Référence Spy ++](../debugger/spy-increment-reference.md) comprend les sections décrivant chaque Spy ++ menu et boîte de dialogue.

 [Ouvrir la vue Messages à partir de la fenêtre Rechercher](../debugger/how-to-open-messages-view-from-find-window.md) explique comment ouvrir la vue Messages à partir de la boîte de dialogue Rechercher une fenêtre.

 [Recherche d’un Message dans la vue Messages](../debugger/how-to-search-for-a-message-in-messages-view.md) explique comment rechercher un message spécifique dans la vue Messages.

 [La vue messages](../debugger/messages-view.md) affiche le flux de message associé à une fenêtre, un processus ou un thread.

 [Vues Spy ++](../debugger/spy-increment-views.md) explique les arborescences Spy ++ de windows, les messages, les processus et les threads.

 [À l’aide de Spy ++](../debugger/using-spy-increment.md) présente l’outil Spy ++ et explique comment il peut être utilisé.