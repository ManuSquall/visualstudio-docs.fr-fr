---
title: "Les caract&#232;res de type ne peuvent pas &#234;tre utilis&#233;s dans des d&#233;clarations de type anonymes | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les caract&#232;res de type ne peuvent pas &#234;tre utilis&#233;s dans des d&#233;clarations de type anonymes
Quand vous déclarez une instance d’un type anonyme, vous ne pouvez pas utiliser un caractère de type sur un nom de propriété. Le type de données de la propriété est déduit à partir de la valeur qui lui est assignée. Par exemple, les déclarations suivantes ne sont pas valides.  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **ID d’erreur :** BC36560  
  
### Pour corriger cette erreur  
  
-   Supprimez le caractère de type de la liste d’initialiseurs. Vous pouvez convertir explicitement la valeur assignée si cela est nécessaire pour établir le type de données voulu pour la propriété.  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)