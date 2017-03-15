---
title: "La propri&#233;t&#233; de membre de type anonyme &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre utilis&#233;e pour d&#233;duire le type d’une autre propri&#233;t&#233; de membre, car le type de &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; n’est pas encore &#233;tabli. | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; de membre de type anonyme &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre utilis&#233;e pour d&#233;duire le type d’une autre propri&#233;t&#233; de membre, car le type de &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; n’est pas encore &#233;tabli.
Tant que le type d’une propriété de type anonyme n’est pas établi, il ne peut pas être utilisé pour établir le type d’une autre propriété. Par exemple, dans la déclaration suivante, `.IDName = .LastName` n’est pas valide, car `.LastName` n’a pas encore été initialisé.  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **ID d’erreur :** BC36559  
  
### Pour corriger cette erreur  
  
-   Établissez le type de la propriété avant de l’utiliser pour initialiser une autre propriété.  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## Voir aussi  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)