---
title: "/Diff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# /Diff
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compare deux fichiers.  Les différences sont affichées dans une fenêtre spéciale de Visual Studio.  
  
## Syntaxe  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],  
[TargetDisplayName]  
```  
  
## Arguments  
 `SourceFile`  
 Requis.  Le chemin d'accès complet et le nom du premier fichier à comparer.  
  
 `TargetFile`  
 Requis.  Le chemin d'accès complet et le nom du deuxième fichier à comparer  
  
 `SourceDisplayName`  
 Optionnel.  Le nom complet du premier fichier.  
  
 `TargetDisplayName`  
 Optionnel.  Le nom complet du deuxième fichier.