---
title: "&#39;Finally&#39; doit se terminer par un &#39;End Try&#39; correspondant | Microsoft Docs"
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
  - "vbc30442"
  - "bc30442"
helpviewer_keywords: 
  - "BC30442"
ms.assetid: 36cce657-186c-4ba0-a760-abcef9529f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; doit se terminer par un &#39;End Try&#39; correspondant
Une instruction `Finally` apparaît dans votre code sans instruction `End Try` correspondante. Les instructions `Finally` doivent se conclure par une instruction `End Try`.  
  
 **ID d’erreur :** BC30442  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction `Finally`.  
  
2.  Ajoutez une instruction `End Try` pour conclure le bloc.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)