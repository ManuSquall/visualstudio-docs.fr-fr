---
title: "D&#233;marrer, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start (commande)"
  - "Démarrer (commande)"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# D&#233;marrer, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Commence à déboguer le projet de démarrage.  
  
## Syntaxe  
  
```  
Debug.Start [address]  
```  
  
## Arguments  
 `address`  
 Facultatif.  Adresse à laquelle le programme suspend son exécution, semblable à un point d'arrêt dans le code source.  Cet argument est valide uniquement en mode débogage.  
  
## Notes  
 Lorsqu'elle est exécutée, la commande **Start** effectue une opération RunToCursor vers l'adresse spécifiée.  
  
## Exemple  
 Cet exemple démarre le débogueur et ignore toute exception qui peut se produire.  
  
```  
>Debug.Start  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)