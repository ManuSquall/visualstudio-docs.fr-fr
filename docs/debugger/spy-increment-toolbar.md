---
title: "Spy++ Toolbar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La barre d'outils s'affiche sous la barre de menus dans Spy\+\+.  Pour afficher ou masquer la barre d'outils, dans le menu **Affichage**, cliquez sur **Barre d'outils**.  
  
 Les contrôles suivants sont disponibles dans la barre d'outils.  
  
## Liste UIElement  
  
|Button|Effet|  
|------------|-----------|  
|![Bouton de la fenêtre Spy&#43;&#43;](~/debugger/media/icon_spy--_windows.gif "Icon\_Spy\+\+\_Windows")|Affiche une arborescence des fenêtres et des contrôles du système.  Pour plus d'informations, consultez [Windows View](../debugger/windows-view.md).|  
|![Bouton Processus Spy&#43;&#43;](~/debugger/media/icon_spy--_processes.gif "Icon\_Spy\+\+\_Processes")|Affiche une arborescence des processus du système.  Pour plus d'informations, consultez [Processes View](../debugger/processes-view.md).|  
|![Bouton Threads Spy&#43;&#43;](~/debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|Affiche une arborescence des threads du système.  Pour plus d'informations, consultez [Threads View](../debugger/threads-view.md).|  
|![Bouton des messages Spy&#43;&#43;](~/debugger/media/icon_spy--_messages.gif "Icon\_Spy\+\+\_Messages")|Crée une fenêtre pour afficher les messages de fenêtre et ouvre la boîte de dialogue **Options des messages** afin que vous puissiez sélectionner la fenêtre dont les messages sont affichés et sélectionner d'autres options.  Pour plus d'informations, consultez [Messages View](../debugger/messages-view.md).|  
|![Bouton de démarrage de la journalisation Spy&#43;&#43;](~/debugger/media/icon_spy--_startlog.gif "Icon\_Spy\+\+\_StartLog")|Démarre l'enregistrement des messages et affiche le flux de messages.  Ce contrôle est disponible uniquement lorsqu'une fenêtre **Messages** est la fenêtre active.  Pour plus d'informations, consultez [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Bouton d'arrêt de la journalisation Spy&#43;&#43;](~/debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|Arrête l'enregistrement des messages et l'affichage du flux de messages.  Ce contrôle est disponible uniquement lorsqu'une fenêtre **Messages** est la fenêtre active.  Pour plus d'informations, consultez [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Bouton d'options du journal Spy&#43;&#43;](~/debugger/media/icon_spy--_logoptions.gif "Icon\_Spy\+\+\_LogOptions")|Affiche la boîte de dialogue [Options des messages](../debugger/message-options-dialog-box.md).  Utilisez cette boîte de dialogue pour sélectionner les fenêtres et les types de messages à afficher.  Ce contrôle est disponible uniquement lorsqu'une fenêtre **Messages** est la fenêtre active.|  
|![Bouton Effacer le journal Spy&#43;&#43;](~/debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|Efface le contenu de la fenêtre **Messages** active.  Ce contrôle est disponible uniquement lorsqu'une fenêtre **Messages** est la fenêtre active.|  
|![Bouton Rechercher une fenêtre Spy&#43;&#43;](~/debugger/media/icon_spy--_findwindow.gif "Icon\_Spy\+\+\_FindWindow")|Ouvre la boîte de dialogue [Rechercher une fenêtre](../debugger/find-window-dialog-box.md) qui vous permet de définir les critères de recherche d'une fenêtre et d'afficher les propriétés ou messages.  Pour plus d'informations, consultez [How to: Use the Finder Tool](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md).|  
|![Bouton Rechercher la première fenêtre Spy&#43;&#43;](~/debugger/media/icon_spy--_window.gif "Icon\_Spy\+\+\_Window")|Recherche dans l'affichage actuel une fenêtre, un processus, un thread ou un message correspondant.|  
|![Bouton Rechercher une fenêtre suivante Spy&#43;&#43;](~/debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|Recherche dans l'affichage actuel la prochaine correspondance de la fenêtre, du processus, du thread ou du message.  Ce contrôle \(et la commande de menu connexe\) est disponible uniquement lorsqu'il existe un résultat de recherche valide qui n'est pas unique.  Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l'arborescence de la fenêtre, des résultats uniques sont générés parce qu'il n'y a qu'une fenêtre dans l'arborescence de la fenêtre qui a ce handle ; dans ce cas, **Suivant** n'est pas disponible.|  
|![Bouton Rechercher une fenêtre précédente Spy&#43;&#43;](~/debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|Recherche dans l'affichage actuel la précédente correspondance de la fenêtre, du processus, du thread ou du message.  Ce contrôle \(et la commande de menu connexe\) est disponible uniquement lorsqu'il existe un résultat de recherche valide qui n'est pas unique.  Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l'arborescence de la fenêtre, des résultats uniques sont générés parce qu'il n'y a qu'une fenêtre dans l'arborescence de la fenêtre qui a ce handle ; dans ce cas, **Précédent** n'est pas disponible.|  
|![Bouton Explorateur des propriétés Spy&#43;&#43;](~/debugger/media/icon_spy--_propexp.gif "Icon\_Spy\+\+\_PropExp")|Affiche les propriétés de la fenêtre qui est sélectionnée dans la vue Fenêtres.|  
|![Bouton Actualiser Spy&#43;&#43;](~/debugger/media/icon_spy--_refresh.gif "Icon\_Spy\+\+\_Refresh")|Actualise les vues système.|  
  
## Voir aussi  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)