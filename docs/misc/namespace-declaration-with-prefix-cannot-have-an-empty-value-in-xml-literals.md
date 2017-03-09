---
title: "Une d&#233;claration d’espace de noms avec pr&#233;fixe ne peut pas avoir une valeur vide dans un litt&#233;ral XML | Microsoft Docs"
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
  - "bc31184"
  - "vbc31184"
helpviewer_keywords: 
  - "BC31184"
ms.assetid: dde656b4-df3b-4a2e-8871-4e14832ca778
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une d&#233;claration d’espace de noms avec pr&#233;fixe ne peut pas avoir une valeur vide dans un litt&#233;ral XML
Une déclaration d’espace de noms XML dans un littéral XML ne comprend pas de valeur d’espace de noms. Par exemple, le code suivant génère cette erreur :  
  
```vb#  
Dim book = <book xmlns:ns=""/>  
```  
  
 **ID d’erreur :** BC31184  
  
### Pour corriger cette erreur  
  
-   Ajoutez un espace de noms valide dans la déclaration d’espace de noms XML ou supprimez la déclaration d’espace de noms XML du littéral XML.  
  
     Vous pouvez également utiliser l’instruction `Imports` pour identifier un préfixe d’espace de noms pour l’espace de noms vide. Exemple :  
  
    ```vb#  
    Imports <xmlns:ns="">  
    ```  
  
## Voir aussi  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)