---
title: "Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.processesview"
helpviewer_keywords: 
  - "Processes view"
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Processus affiche une arborescence de tous les processus actifs sur votre système.  L'ID de processus et le nom de module sont affichés.  Utilisez la vue Processus pour examiner un processus système particulier, lequel correspond habituellement à un programme en cours d'exécution.  Les processus sont identifiés par des noms de modules ou sont désignés en tant que « processus système ».  
  
 Microsoft Windows prend en charge plusieurs processus.  Chaque processus peut avoir un ou plusieurs threads, et chaque thread peut être associé à une ou plusieurs fenêtres de niveau supérieur.  Chaque fenêtre de niveau supérieur peut posséder toute une série de fenêtres.  Le symbole \+ indique qu'un niveau est réduit.  L'affichage réduit se compose d'une ligne par processus.  Cliquez sur le symbole \+ pour développer le niveau.  
  
 Utilisez la vue Processus pour examiner un processus système particulier, lequel correspond habituellement à un programme en cours d'exécution.  Les processus sont identifiés par des noms de modules ou sont désignés en tant que « processus système ». Pour rechercher un processus, réduisez l'arborescence et recherchez dans la liste.  
  
## Procédures  
  
#### Pour ouvrir la vue Processus  
  
1.  Dans le menu **Espionner**, choisissez **Processus**.  
  
 ![Vue Processus Spy&#43;&#43;](../debugger/media/spy--_processes.png "Spy\+\+\_Processes")  
Vue Processus Spy\+\+  
  
 La figure ci\-dessus illustre la vue Processus avec le développement des nœuds processus et thread.  
  
### Dans cette section  
 [Recherche d'un processus dans la vue Processus](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Explique comment rechercher un processus spécifique dans la vue Processus.  
  
 [Affichage des propriétés d'un processus](../debugger/how-to-display-process-properties.md)  
 Explique comment afficher davantage d'informations sur un message.  
  
### Rubriques connexes  
 [Vues Spy\+\+](../debugger/spy-increment-views.md)  
 Explique les arborescences Spy\+\+ des fenêtres, messages, processus et threads.  
  
 [Utilisation de Spy\+\+](../debugger/using-spy-increment.md)  
 Présente l'outil Spy\+\+ et explique comment l'utiliser.  
  
 [Boîte de dialogue Recherche d'un processus](../debugger/process-search-dialog-box.md)  
 Permet de rechercher le nœud d'un processus spécifique dans la vue Processus.  
  
 [Boîte de dialogue Propriétés du processus](../debugger/process-properties-dialog-box.md)  
 Affiche les propriétés d'un processus sélectionné dans la vue Processus.  
  
 [Référence de Spy\+\+](../debugger/spy-increment-reference.md)  
 Inclut des sections décrivant les menus et les boîtes de dialogue de Spy\+\+.