---
title: "Basculer le point d&#39;arr&#234;t, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint (commande)"
  - "Basculer le point d'arrêt (commande)"
  - "ToggleBreakpoint (commande)"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Basculer le point d&#39;arr&#234;t, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Active ou désactive le point d'arrêt, selon son état en cours, à l'emplacement actuel dans le fichier.  
  
## Syntaxe  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## Arguments  
 `text`  
 Facultatif.  Si l'argument text est spécifié, la ligne est marquée en tant que point d'arrêt nommé.  Sinon, la ligne est marquée en tant que point d'arrêt non nommé, ce qui revient à appuyer sur la touche F9.  
  
## Exemple  
 L'exemple suivant bascule le point d'arrêt actuel :  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)