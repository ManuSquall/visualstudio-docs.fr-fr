---
title: "La syntaxe de l’initialiseur d’objet ne peut pas &#234;tre utilis&#233;e pour initialiser une instance de type &#39;Object&#39; | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La syntaxe de l’initialiseur d’objet ne peut pas &#234;tre utilis&#233;e pour initialiser une instance de type &#39;Object&#39;
Vous ne pouvez pas initialiser une instance de `Object` en utilisant la syntaxe de l’initialiseur d’objet. Une instance d’`Object` ne possède pas de propriétés ni de champs auxquels affecter une valeur, et la syntaxe de l’initialiseur d’objet nécessite au moins une propriété ou un champ.  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **ID d’erreur :** BC30994  
  
### Pour corriger cette erreur  
  
1.  Déclarez des instances de type `Object` sans recourir à une liste d’initialiseurs :  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type)