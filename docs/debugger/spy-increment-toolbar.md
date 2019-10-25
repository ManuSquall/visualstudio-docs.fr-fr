---
title: Barre d’outils Spy + + | Microsoft Docs
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
ms.openlocfilehash: 4fa1dfe0917fece3c814678295c5abd6013b426b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729734"
---
# <a name="spy-toolbar"></a>Barre d'outils Spy++
La barre d’outils s’affiche sous la barre de menus dans Spy + +. Pour afficher ou masquer la barre d’outils, dans le menu **affichage** , cliquez sur **barre d’outils**.

 Les contrôles suivants sont disponibles dans la barre d’outils.

## <a name="uielement-list"></a>Liste des éléments d’interface

|Button|Effet|
|------------|------------|
|![Bouton&#43; &#43; fenêtres Spy](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Affiche une arborescence des fenêtres et des contrôles du système. Pour plus d’informations, consultez [vue Windows](../debugger/windows-view.md).|
|![Bouton&#43; &#43; processus Spy](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Affiche une arborescence des processus dans le système. Pour plus d’informations, consultez [vue processus](../debugger/processes-view.md).|
|![Bouton&#43; &#43; threads Spy](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Affiche une arborescence des threads dans le système. Pour plus d’informations, consultez [vue threads](../debugger/threads-view.md).|
|![Bouton&#43; &#43; messages Spy](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + Inline")|Crée une fenêtre pour afficher des messages de fenêtre et ouvre la boîte de dialogue **Options des messages** pour vous permettre de sélectionner la fenêtre dont les messages seront affichés et de sélectionner également d’autres options. Pour plus d’informations, consultez [vue messages](../debugger/messages-view.md).|
|![Bouton&#43; &#43; du journal de démarrage Spy](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Démarre l’enregistrement des messages et affiche le flux de message. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active. Pour plus d’informations, consultez [procédure : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Bouton&#43; &#43; du journal d’arrêt Spy](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Arrête l’enregistrement des messages et l’affichage du flux de messages. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active. Pour plus d’informations, consultez [procédure : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Bouton&#43; &#43; options du journal Spy](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Affiche la boîte de dialogue [Options des messages](../debugger/message-options-dialog-box.md) . Utilisez cette boîte de dialogue pour sélectionner des fenêtres et des types de messages à afficher. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active.|
|![Bouton&#43; &#43; effacer le journal de l’espionnage](../debugger/media/spy--_clearlog.gif "_ClearLog Spy + +")|Efface le contenu de la fenêtre **messages** actifs. Ce contrôle est disponible uniquement lorsqu’une fenêtre **messages** est la fenêtre active.|
|![Bouton&#43; &#43; de la fenêtre Rechercher Spy](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Ouvre la boîte de dialogue [Rechercher une fenêtre](../debugger/find-window-dialog-box.md) , qui vous permet de définir des critères de recherche de fenêtre et d’afficher des propriétés ou des messages. Pour plus d’informations, consultez [Comment : utiliser l’outil Finder](../debugger/how-to-use-the-finder-tool.md).|
|![Bouton&#43; &#43; de recherche de la première fenêtre Spy](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Recherche la vue actuelle d’une fenêtre, d’un processus, d’un thread ou d’un message correspondant.|
|![Bouton&#43; &#43; Spy Rechercher la fenêtre suivante](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Recherche la fenêtre, le processus, le thread ou le message suivant. Ce contrôle (et la commande de menu associée) est disponible uniquement lorsqu’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il produit des résultats uniques, car il n’existe qu’une seule fenêtre dans l’arborescence de la fenêtre qui contient ce handle ; dans cette instance, l' **étape suivante** n’est pas disponible.|
|![Bouton&#43; &#43; Spy Rechercher la fenêtre précédente](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Recherche la vue actuelle de la fenêtre, du processus, du thread ou du message précédent. Ce contrôle (et la commande de menu associée) est disponible uniquement lorsqu’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il produit des résultats uniques, car il n’existe qu’une seule fenêtre dans l’arborescence de la fenêtre qui contient ce handle ; dans ce cas, la **recherche précédente** n’est pas disponible.|
|![Bouton&#43; &#43; de l’Explorateur de propriétés Spy](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Affiche les propriétés de la fenêtre sélectionnée dans la vue fenêtres.|
|![Bouton&#43; &#43; actualisation Spy](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Actualise les vues système.|

## <a name="see-also"></a>Voir aussi
- [Utilisation de Spy++](../debugger/using-spy-increment.md)
- [Vues Spy++](../debugger/spy-increment-views.md)
- [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)