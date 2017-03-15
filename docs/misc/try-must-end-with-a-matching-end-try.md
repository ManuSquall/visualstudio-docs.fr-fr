---
title: "&#39;Try&#39; doit se terminer par un &#39;End Try&#39; correspondant | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Try&#39; doit se terminer par un &#39;End Try&#39; correspondant
`Try` sert à initier un bloc `Try`. Il ne peut donc apparaître qu’au début du bloc, avec une instruction`End Try` correspondante à la fin du bloc. Soit vous avez un `Try` redondant, soit vous n’avez pas terminé votre bloc `Try` avec `Finally`.  
  
 **ID d’erreur :** BC30384  
  
### Pour corriger cette erreur  
  
1.  Recherchez et supprimez le `Try` superflu, ou terminez le bloc avec un `End Try` correspondant.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)