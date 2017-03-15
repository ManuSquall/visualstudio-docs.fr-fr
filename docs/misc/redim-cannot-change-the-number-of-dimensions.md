---
title: "&#39;ReDim&#39; ne peut pas changer le nombre de dimensions | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArray_RankMismatch"
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; ne peut pas changer le nombre de dimensions
Une opération tente d’utiliser l’instruction `ReDim` pour modifier le rang \(nombre de dimensions\) d’un tableau. L’instruction `ReDim` peut modifier la taille d’une ou plusieurs dimensions d’un tableau qui a déjà été déclaré en bonne et due forme, mais elle ne peut pas modifier le rang d’un tableau.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous de bien vouloir modifier le rang du tableau et non la taille de ses dimensions et, si possible, utilisez `Dim` pour déclarer un nouveau tableau avec le rang souhaité.  
  
## Voir aussi  
 [NOTINBUILD Vue d’ensemble des tableaux en Visual Basic](http://msdn.microsoft.com/fr-fr/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD Tableaux multidimensionnels en Visual Basic](http://msdn.microsoft.com/fr-fr/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)