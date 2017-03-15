---
title: "D&#233;finir la base, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix (commande)"
  - "Définir la base (commande)"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# D&#233;finir la base, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit ou retourne la base numérique utilisée pour afficher les valeurs entières.  
  
## Syntaxe  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## Arguments  
 `10` ou `16` ou `hex` ou `dec`  
 Facultatif.  Indique un nombre décimal \(10 ou dec\) ou hexadécimal \(16 ou hex\).  Si l'argument est omis, cette commande retourne la base numérique en cours.  
  
## Exemple  
 Cet exemple configure l'environnement pour afficher les valeurs entières au format hexadécimal.  
  
```  
>Debug.SetRadix hex  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)