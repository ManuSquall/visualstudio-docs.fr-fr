---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez rechercher un thread spécifique dans la vue Threads en utilisant son ID de thread ou sa chaîne de module comme critère de recherche.  Vous pouvez également spécifier la direction initiale de la recherche.  Les champs de la boîte de dialogue affichent les attributs du thread sélectionné dans l'arborescence des threads.  
  
### Pour rechercher un thread dans la vue Threads  
  
1.  Réorganisez vos fenêtres afin que Spy\+\+ et une fenêtre [Vue Threads](../debugger/threads-view.md) active soient visibles.  
  
2.  Dans le menu **Rechercher**, choisissez **Rechercher le thread**.  
  
     La [boîte de dialogue Recherche d'un thread](../debugger/thread-search-dialog-box.md) s'ouvre.  
  
3.  Tapez l'ID de thread ou une chaîne de module comme critère de recherche.  
  
4.  Désactivez les champs pour lesquels vous ne voulez pas spécifier de valeurs.  
  
    > [!TIP]
    >  Pour rechercher tous les threads détenus par un module, effacez le contenu de la zone de texte **Thread** et tapez le nom du module dans la zone **Module**.  Utilisez ensuite **Suivant** pour continuer à rechercher des threads.  
  
5.  Sélectionnez **Haut** ou **Bas** comme direction initiale de la recherche.  
  
6.  Cliquez sur **OK**.  
  
 Si un thread correspondant est trouvé, il est mis en surbrillance dans la fenêtre Vue Threads.