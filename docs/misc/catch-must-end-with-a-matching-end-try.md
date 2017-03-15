---
title: "&#39;Catch&#39; doit se terminer par un &#39;End Try&#39; correspondant | Microsoft Docs"
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
  - "bc30441"
  - "vbc30441"
helpviewer_keywords: 
  - "BC30441"
ms.assetid: 0e4756b4-1f29-4073-88c5-8f8c93ba6c9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; doit se terminer par un &#39;End Try&#39; correspondant
Une instruction `Catch` apparaît dans votre code sans instruction `End Try` correspondante. Les instructions `Catch` doivent se conclure par une instruction `End Try`.  
  
 **ID d’erreur :** BC30441  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction `Catch`.  
  
2.  Ajoutez une instruction `End Try` pour conclure le bloc.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)