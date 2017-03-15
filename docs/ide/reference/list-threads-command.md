---
title: "Afficher les threads, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads (commande)"
  - "Afficher les threads (commande)"
  - "ListThreads (commande)"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Afficher les threads, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche la liste des threads du programme en cours.  
  
## Syntaxe  
  
```  
Debug.ListThreads [index]  
```  
  
## Arguments  
 `index`  
 Facultatif.  Sélectionne un thread par son index pour en faire le thread actuel.  
  
## Notes  
 Une fois spécifié, l'argument `index` marque le thread indiqué comme étant le thread actuel.  Un astérisque \(\*\) est affiché dans la liste à côté du thread actuel.  
  
## Exemple  
  
```  
>Debug.ListThreads   
```  
  
## Voir aussi  
 [Afficher la pile d'appels, commande](../../ide/reference/list-call-stack-command.md)   
 [Afficher le code machine, commande](../../ide/reference/list-disassembly-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)