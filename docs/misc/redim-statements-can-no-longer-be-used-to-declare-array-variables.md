---
title: "Les instructions &#39;ReDim&#39; ne peuvent plus &#234;tre utilis&#233;es pour d&#233;clarer des variables tableau | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;ReDim&#39; ne peuvent plus &#234;tre utilis&#233;es pour d&#233;clarer des variables tableau
`ReDim` peut uniquement être utilisé pour modifier la taille d’un tableau existant.  
  
 **ID d’erreur :** BC30811  
  
### Pour corriger cette erreur  
  
-   Spécifiez la taille des tableaux quand ils sont déclarés. Par exemple :  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## Voir aussi  
 [Arrays Summary](/dotnet/visual-basic/language-reference/keywords/arrays-summary)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/b4da14db-ff23-490f-b3c6-d7ae1b649532)