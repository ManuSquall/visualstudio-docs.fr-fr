---
title: "D&#233;finir le processus actuel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debug.SetCurrentProcess (commande)"
  - "Définir le processus actuel (commande)"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# D&#233;finir le processus actuel
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit le processus spécifié comme processus actif dans le débogueur.  
  
## Syntaxe  
  
```  
Debug.SetCurrentProcess index  
```  
  
## Arguments  
 `index`  
 Requis.  Index du processus.  
  
## Notes  
 Pendant un débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l'un d'entre eux est actif dans le débogueur à un moment donné.  Vous pouvez utiliser la commande `SetCurrentProcess` pour définir un processus actif.  
  
## Exemple  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)