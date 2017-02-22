---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez rechercher un processus spécifique dans la vue Processus en utilisant son ID de processus ou sa chaîne de module comme critère de recherche.  Vous pouvez également spécifier la direction initiale de la recherche.  Les champs de la boîte de dialogue affichent les attributs du processus sélectionné dans l'arborescence des processus.  
  
### Pour rechercher un processus dans la vue Processus  
  
1.  Réorganisez vos fenêtres afin que Spy\+\+ et une fenêtre [Vue Processus](../debugger/processes-view.md) active soient visibles.  
  
2.  Dans le menu **Rechercher**, choisissez **Rechercher le processus**.  
  
     La [boîte de dialogue Recherche d'un processus](../debugger/process-search-dialog-box.md) s'ouvre.  
  
3.  Tapez l'ID de processus ou une chaîne de module comme critère de recherche.  
  
4.  Désactivez les champs pour lesquels vous ne voulez pas spécifier de valeurs.  
  
    > [!TIP]
    >  Pour rechercher tous les processus détenus par un module, effacez le contenu de la zone de texte **Processus** et tapez le nom du module dans la zone **Module**.  Utilisez ensuite **Suivant** pour continuer à rechercher des processus.  
  
5.  Sélectionnez **Haut** ou **Bas** comme direction initiale de la recherche.  
  
6.  Cliquez sur **OK**.  
  
 Si un processus correspondant est trouvé, il est mis en surbrillance dans la fenêtre **Vue Processus**.