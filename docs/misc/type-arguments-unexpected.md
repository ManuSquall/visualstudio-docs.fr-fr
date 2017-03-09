---
title: "Arguments de type inattendus | Microsoft Docs"
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
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arguments de type inattendus
Une clause `Implements` fournit des arguments de type pour le membre d’interface qu’elle implémente.  
  
 La clause `Implements` doit identifier uniquement l’interface et le membre qu’elle implémente. Cela signifie que si vous déclarez une procédure générique, la clause `Of` et les arguments de type doivent apparaître dans la partie principale de la déclaration, comme ce serait le cas si vous n’implémentiez pas une procédure d’interface.  
  
 Le code suivant peut générer cette erreur.  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 La déclaration qui précède la clause `Implements` doit ressembler à la définition d’interface, à l’exception d’éventuels modificateurs d’accès ou de procédure. Le code suivant permet d’éviter cette erreur.  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **ID d’erreur :** BC32088  
  
### Pour corriger cette erreur  
  
-   Supprimez la liste d’arguments de type de la clause `Implements`.  
  
-   Si vous implémentez un membre générique de l’interface, placez la liste d’arguments de type dans la partie principale de la déclaration, avant le mot clé `Implements`.  
  
## Voir aussi  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NOT IN BUILD : Implements, mot clé et instruction](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)