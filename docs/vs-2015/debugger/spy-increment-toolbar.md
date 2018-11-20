---
title: Barre d’outils Spy ++ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05dc7dd74af20c76a3b673d5960cd88331ad7d51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763325"
---
# <a name="spy-toolbar"></a>Barre d'outils Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La barre d’outils apparaît sous la barre de menus dans Spy ++. Pour afficher ou masquer la barre d’outils, sur le **vue** menu, cliquez sur **barre d’outils**.  
  
 Les contrôles suivants sont disponibles sur la barre d’outils.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
  
|Bouton|Effet|  
|------------|------------|  
|![Spy&#43; &#43; Windows bouton](../debugger/media/icon-spy-windows.gif "Icon_Spy ++ _Windows")|Affiche une arborescence des fenêtres et des contrôles dans le système. Pour plus d’informations, consultez [Windows vue](../debugger/windows-view.md).|  
|![Spy&#43; &#43; traite bouton](../debugger/media/icon-spy-processes.gif "Icon_Spy ++ _Processes")|Affiche une arborescence des processus dans le système. Pour plus d’informations, consultez [vue processus](../debugger/processes-view.md).|  
|![Spy&#43; &#43; Threads bouton](../debugger/media/icon-spy-threads.gif "Icon_Spy ++ _Threads")|Affiche une arborescence des threads dans le système. Pour plus d’informations, consultez [vue Threads](../debugger/threads-view.md).|  
|![Spy&#43; &#43; Messages bouton](../debugger/media/icon-spy-messages.gif "Icon_Spy ++ _Messages")|Crée une fenêtre pour afficher les messages de fenêtre et ouvre le **Options des messages** afin que vous puissiez sélectionner la fenêtre dont les messages seront affiche et sélectionner d’autres options de boîte de dialogue. Pour plus d’informations, consultez [vue Messages](../debugger/messages-view.md).|  
|![Spy&#43; &#43; bouton Démarrer le journal](../debugger/media/icon-spy-startlog.gif "Icon_Spy ++ _StartLog")|Démarre la journalisation des messages et affiche le flux de message. Ce contrôle est disponible uniquement quand un **Messages** fenêtre est la fenêtre active. Pour plus d’informations, consultez [Comment : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; journal bouton Arrêter](../debugger/media/icon-spy-stoplog.gif "Icon_Spy ++ _StopLog")|Journalisation et l’affichage du flux de messages des messages s’arrête. Ce contrôle est disponible uniquement quand un **Messages** fenêtre est la fenêtre active. Pour plus d’informations, consultez [Comment : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; Options bouton journaux](../debugger/media/icon-spy-logoptions.gif "Icon_Spy ++ _LogOptions")|Affiche le [Options des messages](../debugger/message-options-dialog-box.md) boîte de dialogue. Utilisez cette boîte de dialogue pour sélectionner windows et de types pour l’affichage de messages. Ce contrôle est disponible uniquement quand un **Messages** fenêtre est la fenêtre active.|  
|![Spy&#43; &#43; journal bouton Effacer](../debugger/media/spy-clearlog.gif "Spy ++ _ClearLog")|Efface le contenu de l’actif **Messages** fenêtre. Ce contrôle est disponible uniquement quand un **Messages** fenêtre est la fenêtre active.|  
|![Spy&#43; &#43; trouver le bouton de la fenêtre](../debugger/media/icon-spy-findwindow.gif "Icon_Spy ++ _FindWindow")|Ouvre le [rechercher une fenêtre](../debugger/find-window-dialog-box.md) boîte de dialogue qui vous permet de définir des critères de recherche de fenêtre et afficher les propriétés ou les messages. Pour plus d’informations, consultez [Comment : utiliser l’outil recherche](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; rechercher le premier bouton de fenêtre](../debugger/media/icon-spy-window.gif "Icon_Spy ++ _Window")|Recherche dans la vue actuelle pour une correspondance de la fenêtre, le processus, le thread ou le message.|  
|![Spy&#43; &#43; bouton de fenêtre suivant](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy ++ _NextWindow")|Recherche dans la vue actuelle pour la fenêtre correspondante suivante, le processus, le thread ou le message. Ce contrôle (et la commande de menu associés) sont disponibles uniquement s’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il génère des résultats uniques, car il n’est qu’une seule fenêtre dans l’arborescence de la fenêtre qui a ce handle ; Dans ce cas, **suivant** n’est pas disponible.|  
|![Spy&#43; &#43; trouver le bouton précédent de la fenêtre](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy ++ _PrevWindow")|Recherche dans la vue actuelle pour la fenêtre correspondante précédente, le processus, le thread ou le message. Ce contrôle (et la commande de menu associés) sont disponibles uniquement s’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il génère des résultats uniques, car il n’est qu’une seule fenêtre dans l’arborescence de la fenêtre qui a ce handle ; Dans ce cas, **précédent** n’est pas disponible.|  
|![Spy&#43; &#43; bouton Explorateur des propriétés](../debugger/media/icon-spy-propexp.gif "Icon_Spy ++ _PropExp")|Affiche les propriétés de la fenêtre qui est sélectionné dans la vue de Windows.|  
|![Spy&#43; &#43; bouton Actualiser](../debugger/media/icon-spy-refresh.gif "Icon_Spy ++ _actualiser")|Actualise les vues système.|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Spy ++](../debugger/using-spy-increment.md)   
 [Vues Spy ++](../debugger/spy-increment-views.md)   
 [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)



