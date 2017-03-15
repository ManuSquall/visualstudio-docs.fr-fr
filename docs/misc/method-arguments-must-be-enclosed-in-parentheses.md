---
title: "Les arguments de m&#233;thode doivent &#234;tre mis entre parenth&#232;ses | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30800"
  - "bc30800"
helpviewer_keywords: 
  - "BC30800"
ms.assetid: ecdec760-8b51-474f-acad-17cf8059d83b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de m&#233;thode doivent &#234;tre mis entre parenth&#232;ses
Les règles qui régissent les appels de procédure sont plus simples dans les dernières versions de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Tous les arguments doivent être mis entre parenthèses.  
  
 **ID d’erreur :** BC30800  
  
### Pour corriger cette erreur  
  
-   Mettez la liste d’arguments entre parenthèses, par exemple :  
  
    ```  
    MySub(ArrayIndex, NewValue)  
    ```  
  
## Voir aussi  
 [Procedure Calling Sequence Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/4ef1eea6-36cb-4b97-a31b-9ba65e46a9fd)   
 [Procedure Parameters and Arguments](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)