---
title: "Des attributs ne peuvent pas &#234;tre appliqu&#233;s aux param&#232;tres d’expressions lambda | Microsoft Docs"
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
  - "vbc36634"
  - "bc36634"
helpviewer_keywords: 
  - "BC36634"
ms.assetid: ed751d8d-11b7-4210-97e0-0319edff8c34
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Des attributs ne peuvent pas &#234;tre appliqu&#233;s aux param&#232;tres d’expressions lambda
Vous avez appliqué un attribut à un paramètre dans une définition d’expression lambda, ce qui n’est pas pris en charge. Le code suivant génère cette erreur.  
  
```vb#  
Sub LambaAttribute()  
    ' Not valid.  
    Dim add1 = _  
    Function(<System.Runtime.InteropServices.InAttribute()> m As Integer) _  
                   m + 1  
End Sub  
```  
  
 **ID d’erreur :** BC36634  
  
### Pour corriger cette erreur  
  
-   Supprimez l’attribut, ou envisagez de modifier votre code en remplaçant l’expression lambda par une fonction régulière.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.InAttribute>   
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)