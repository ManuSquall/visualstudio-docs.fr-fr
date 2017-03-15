---
title: "Le param&#232;tre de type n’est pas autoris&#233; dans la clause &#39;Implements&#39; | Microsoft Docs"
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
  - "vbc32056"
  - "bc32056"
helpviewer_keywords: 
  - "BC32056"
ms.assetid: a62d773b-e878-4817-8638-da49849477d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type n’est pas autoris&#233; dans la clause &#39;Implements&#39;
Une clause `Implements` dans un type générique spécifie un paramètre de type comme le membre à implémenter.  
  
 Une clause `Implements` doit spécifier une interface et un membre. Elle peut passer un paramètre de type à l’interface, mais elle ne peut pas le passer au membre, ni l’utiliser comme nom du membre.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Class c1(Of t) Implements i1(Of t) Public Sub doSomething() Implements t End Class  
```  
  
 **ID d'erreur :** BC32056  
  
### Pour corriger cette erreur  
  
-   Spécifiez le nom d’interface et un membre authentique de l’interface après le mot clé `Implements`. Vous pouvez passer le paramètre de type à l’interface, si nécessaire.  
  
    ```  
    Public Sub doSomething() Implements i1(Of t).doSomething  
    ```  
  
## Voir aussi  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NOT IN BUILD : Implements, mot clé et instruction](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)