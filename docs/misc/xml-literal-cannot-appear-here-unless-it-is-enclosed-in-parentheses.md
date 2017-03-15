---
title: "Un litt&#233;ral XML ne peut pas s’afficher ici &#224; moins qu’il ne soit mis entre parenth&#232;ses | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un litt&#233;ral XML ne peut pas s’afficher ici &#224; moins qu’il ne soit mis entre parenth&#232;ses
Une déclaration de littéral XML est utilisée dans une expression, à un emplacement ambigu pour le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Autrement dit, le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas déterminer si le caractère inférieur à \(\<\) est un opérateur de comparaison ou le début d’un littéral XML. Le code suivant est fourni à titre d'exemple :  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **ID d’erreur :** BC31198  
  
### Pour corriger cette erreur  
  
-   Placez la déclaration de littéral XML entre parenthèses, comme illustré dans l’exemple suivant :  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   Modifiez votre code pour référencer un littéral XML existant, comme illustré dans l’exemple suivant :  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## Voir aussi  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)