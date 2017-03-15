---
title: "Une expression ne peut pas s’afficher &#224; l’int&#233;rieur d’une valeur d’attribut entre guillemets | Microsoft Docs"
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
  - "bc31155"
  - "vbc31155"
helpviewer_keywords: 
  - "BC31155"
ms.assetid: ed3e618e-de94-4e4e-afaf-72b11073fb1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une expression ne peut pas s’afficher &#224; l’int&#233;rieur d’une valeur d’attribut entre guillemets
Une expression ne peut pas s’afficher à l’intérieur d’une valeur d’attribut entre guillemets. Supprimez les guillemets.  
  
 Une expression incorporée dans une valeur d’attribut pour un littéral XML est placée entre guillemets.  
  
 **ID d’erreur :** BC31155  
  
### Pour corriger cette erreur  
  
-   Supprimez les guillemets de délimitation dans la valeur d’attribut. Voici un exemple :  
  
    ```vb#  
    ' Generates an error. Dim elem = <outer attr="<%= value %>" /> ' Does not generate an error. Dim elem = <outer attr=<%= value %> />  
    ```  
  
## Voir aussi  
 [Embedded Expressions in XML](/dotnet/visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)