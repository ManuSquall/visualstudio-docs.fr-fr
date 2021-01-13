---
title: Barre d’outils Spy + + | Microsoft Docs
description: Comprenez les éléments de l’interface utilisateur dans la barre d’outils Spy + +, qui apparaît sous la barre de menus. Pour afficher ou masquer la barre d’outils, dans le menu Affichage, cliquez sur barre d’outils.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dc2564a69c291055d53e358c084e7dd9c4d0506
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148193"
---
# <a name="spy-toolbar"></a>Barre d'outils Spy++
La barre d’outils s’affiche sous la barre de menus dans Spy + +. Pour afficher ou masquer la barre d’outils, dans le menu **affichage** , cliquez sur **barre d’outils**.

 Les contrôles suivants sont disponibles dans la barre d’outils.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

|Bouton|Résultat|
|------------|------------|
|![Bouton fenêtres Spy&#43;&#43; ](../debugger/media/icon_spy--_windows.gif "_Windows Icon_Spy + +")|Affiche une arborescence des fenêtres et des contrôles du système. Pour plus d’informations, consultez [vue Windows](../debugger/windows-view.md).|
|![Bouton processus de&#43;&#43; Spy](../debugger/media/icon_spy--_processes.gif "_Processes Icon_Spy + +")|Affiche une arborescence des processus dans le système. Pour plus d’informations, consultez [vue processus](../debugger/processes-view.md).|
|![Bouton de threads Spy&#43;&#43; ](../debugger/media/icon_spy--_threads.gif "_Threads Icon_Spy + +")|Affiche une arborescence des threads dans le système. Pour plus d’informations, consultez [vue threads](../debugger/threads-view.md).|
|![Bouton messages d'&#43;&#43; Spy](../debugger/media/icon_spy--_messages.gif "_Messages Icon_Spy + +")|Crée une fenêtre pour afficher des messages de fenêtre et ouvre la boîte de dialogue **Options des messages** pour vous permettre de sélectionner la fenêtre dont les messages seront affichés et de sélectionner également d’autres options. Pour plus d’informations, consultez [vue messages](../debugger/messages-view.md).|
|![Bouton de démarrage du journal Spy&#43;&#43; ](../debugger/media/icon_spy--_startlog.gif "_StartLog Icon_Spy + +")|Démarre l’enregistrement des messages et affiche le flux de message. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active. Pour plus d’informations, consultez [procédure : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Bouton d’arrêt du journal d'&#43;&#43; Spy](../debugger/media/icon_spy--_stoplog.gif "_StopLog Icon_Spy + +")|Arrête l’enregistrement des messages et l’affichage du flux de messages. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active. Pour plus d’informations, consultez [procédure : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Bouton Options du journal Spy&#43;&#43; ](../debugger/media/icon_spy--_logoptions.gif "_LogOptions Icon_Spy + +")|Affiche la boîte de dialogue [Options des messages](../debugger/message-options-dialog-box.md) . Utilisez cette boîte de dialogue pour sélectionner des fenêtres et des types de messages à afficher. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active.|
|![Bouton Effacer le journal de&#43;&#43; Spy](../debugger/media/spy--_clearlog.gif "_ClearLog Spy + +")|Efface le contenu de la fenêtre **messages** actifs. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active.|
|![Bouton de la fenêtre Rechercher le&#43;&#43; Spy](../debugger/media/icon_spy--_findwindow.gif "_FindWindow Icon_Spy + +")|Ouvre la boîte de dialogue [Rechercher une fenêtre](../debugger/find-window-dialog-box.md) , qui vous permet de définir des critères de recherche de fenêtre et d’afficher des propriétés ou des messages. Pour plus d’informations, consultez [Comment : utiliser l’outil Finder](../debugger/how-to-use-the-finder-tool.md).|
|![Bouton espion&#43;&#43; Rechercher la première fenêtre](../debugger/media/icon_spy--_window.gif "_Window Icon_Spy + +")|Recherche la vue actuelle d’une fenêtre, d’un processus, d’un thread ou d’un message correspondant.|
|![Espion&#43;&#43; bouton Rechercher la fenêtre suivante](../debugger/media/icon_spy--_nextwindow.gif "_NextWindow Icon_Spy + +")|Recherche la fenêtre, le processus, le thread ou le message suivant. Ce contrôle (et la commande de menu associée) est disponible uniquement lorsqu’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il produit des résultats uniques, car il n’existe qu’une seule fenêtre dans l’arborescence de la fenêtre qui contient ce handle ; dans cette instance, l' **étape suivante** n’est pas disponible.|
|![Espion&#43;&#43; bouton Rechercher la fenêtre précédente](../debugger/media/icon_spy--_prevwindow.gif "_PrevWindow Icon_Spy + +")|Recherche la vue actuelle de la fenêtre, du processus, du thread ou du message précédent. Ce contrôle (et la commande de menu associée) est disponible uniquement lorsqu’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il produit des résultats uniques, car il n’existe qu’une seule fenêtre dans l’arborescence de la fenêtre qui contient ce handle ; dans ce cas, la **recherche précédente** n’est pas disponible.|
|![Bouton de l’Explorateur de propriétés de&#43;&#43; Spy](../debugger/media/icon_spy--_propexp.gif "_PropExp Icon_Spy + +")|Affiche les propriétés de la fenêtre sélectionnée dans la vue fenêtres.|
|![Bouton actualiser l'&#43;&#43; Spy](../debugger/media/icon_spy--_refresh.gif "_Refresh Icon_Spy + +")|Actualise les vues système.|

## <a name="see-also"></a>Voir aussi
- [Utiliser Spy++](../debugger/using-spy-increment.md)
- [Vues Spy++](../debugger/spy-increment-views.md)
- [Référence Spy++](../debugger/spy-increment-reference.md)