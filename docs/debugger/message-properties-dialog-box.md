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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62846113"
---
# <a name="message-properties-dialog-box"></a>Boîte de dialogue Propriétés du message
Utilisez cette boîte de dialogue pour en savoir plus sur un message spécifique. Pour afficher cette boîte de dialogue, déplacez le focus vers une fenêtre d' [affichage des messages](../debugger/messages-view.md) . Sélectionnez un nœud de message dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .

 L’onglet **général** est le seul onglet affiché. Les options suivantes sont disponibles :

 **Handle de fenêtre** ID unique de cette fenêtre. Les numéros de handles de fenêtre sont réutilisés ; ils identifient une fenêtre uniquement pendant la durée de vie de cette fenêtre. Cliquez sur cette valeur pour afficher les propriétés de cette fenêtre.

 **Niveau d’imbrication** Profondeur d’imbrication de ce message, où 0 n’est pas une imbrication.

 **Message** Nombre, État et nom du message Windows sélectionné.

 **LRESULT** Valeur du paramètre *LRESULT* , le cas échéant.

 **wParam** Valeur du paramètre *wParam* , le cas échéant.

 **lParam** Valeur du paramètre *lParam* , le cas échéant. Cette valeur est décodée s’il s’agit d’un pointeur vers une chaîne ou une structure.

## <a name="related-sections"></a>Sections connexes
 [Boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md) Permet de sélectionner les messages qui sont répertoriés dans la vue messages actifs.

 [Boîte de dialogue recherche](../debugger/message-search-dialog-box.md) d’un message Utilisé pour rechercher le nœud pour un message spécifique dans la vue messages.

 [Référence Spy + +](../debugger/spy-increment-reference.md) Comprend des sections décrivant chaque menu et boîte de dialogue Spy + +.

 [Ouverture de la vue messages à partir de la fenêtre Rechercher](../debugger/how-to-open-messages-view-from-find-window.md) Explique comment ouvrir la vue messages à partir de la boîte de dialogue Rechercher une fenêtre.

 [Recherche d’un message dans la vue messages](../debugger/how-to-search-for-a-message-in-messages-view.md) Explique comment rechercher un message spécifique dans la vue messages.

 [Vue messages](../debugger/messages-view.md) Affiche le flux de message associé à une fenêtre, un processus ou un thread.

 [Vues Spy + +](../debugger/spy-increment-views.md) Explique les vues de l’arborescence Spy + + des fenêtres, des messages, des processus et des threads.

 [Utilisation de Spy + +](../debugger/using-spy-increment.md) Présente l’outil Spy + + et explique comment l’utiliser.