---
title: "’ReDim’ ne peut pas changer le nombre de dimensions d’un tableau | Microsoft Docs"
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
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ’ReDim’ ne peut pas changer le nombre de dimensions d’un tableau
Vous avez tenté d’utiliser `ReDim` pour modifier le rang \(nombre de dimensions\) d’un tableau. Vous pouvez utiliser l’instruction `ReDim` pour modifier la taille d’une ou plusieurs dimensions d’un tableau qui a déjà été déclaré formellement, mais pas pour modifier le rang d’un tableau.  
  
 **ID d’erreur :** BC30415  
  
### Pour corriger cette erreur  
  
-   Soyez sûr de bien vouloir obtenir le rang plutôt que la taille du tableau et, si possible, utilisez `Dim` pour déclarer un nouveau tableau avec le rang souhaité.  
  
## Voir aussi  
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NOTINBUILD Vue d’ensemble des tableaux en Visual Basic](http://msdn.microsoft.com/fr-fr/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)