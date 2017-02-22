---
title: "Chemin d&#39;acc&#232;s aux symboles, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath (commande)"
  - "chemin d'accès aux symboles (commande)"
  - "SymbolPath (commande)"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Chemin d&#39;acc&#232;s aux symboles, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit la liste des répertoires dans lesquels le débogueur recherchera des symboles.  
  
## Syntaxe  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## Arguments  
 `pathname`  
 Optionnel.  Liste de chemins d'accès délimités par des points\-virgules dans laquelle le débogueur recherchera des symboles.  
  
## Notes  
 Si aucun `pathname` n'est spécifié, la commande répertorie les chemins d'accès aux symboles actuels.  
  
## Exemple  
 Cet exemple ajoute deux chemins d'accès à la liste des répertoires de symboles.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## Exemple  
 Cet exemple affiche une liste de chemins d'accès des symboles actuels délimités par des points\-virgules.  
  
```  
Debug.SymbolPath  
```  
  
## Voir aussi  
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)