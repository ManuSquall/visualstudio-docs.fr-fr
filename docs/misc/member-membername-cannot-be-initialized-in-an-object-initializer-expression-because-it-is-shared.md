---
title: "Le membre &#39;&lt;nom_membre&gt;&#39; ne peut pas &#234;tre initialis&#233; dans une expression d’initialiseur d’objet, car il est partag&#233; | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_membre&gt;&#39; ne peut pas &#234;tre initialis&#233; dans une expression d’initialiseur d’objet, car il est partag&#233;
Vous ne pouvez pas utiliser des initialiseurs d’objets pour initialiser un membre d’une classe déclaré comme étant partagé. Pour plus d'informations, consultez [Shared](/dotnet/visual-basic/language-reference/modifiers/shared).  
  
 **ID d’erreur :** BC30991  
  
### Pour corriger cette erreur  
  
1.  Examinez la définition de classe pour identifier le membre qui est partagé.  
  
2.  Supprimez l’initialisation de ce membre dans la liste d’initialiseurs d’objets.  
  
## Exemple  
 Dans l’exemple suivant, `totalCustomers` est un membre partagé.  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 Étant donné que `totalCustomers` est partagé, toute tentative de définition de sa valeur initiale dans une liste d’initialiseurs d’objets provoque cette erreur.  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NOT IN BUILD : Membres partagés en Visual Basic](http://msdn.microsoft.com/fr-fr/dbc3783f-83a2-4225-995d-c2d6d025663d)