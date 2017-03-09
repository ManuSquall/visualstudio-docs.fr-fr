---
title: "Identificateur attendu, pr&#233;c&#233;d&#233; d’un point | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Identificateur attendu, pr&#233;c&#233;d&#233; d’un point
Une valeur de laquelle il n’est pas possible de déduire un nom de propriété a été incluse dans la liste d’initialiseurs d’une déclaration de type anonyme, alors qu’elle n’a pas été assignée à un nom de propriété.  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **ID d’erreur :** BC36576  
  
### Pour corriger cette erreur  
  
-   Fournissez un nom de propriété pour chaque valeur de la liste d’initialiseurs, comme indiqué dans le code suivant :  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## Voir aussi  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Comment : déclarer une instance d’un type anonyme \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)