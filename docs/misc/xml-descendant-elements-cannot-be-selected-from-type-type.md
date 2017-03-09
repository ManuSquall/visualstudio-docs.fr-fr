---
title: "Les &#233;l&#233;ments descendants XML ne peuvent pas &#234;tre s&#233;lectionn&#233;s &#224; partir du type &#39;type&#39; | Microsoft Docs"
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
  - "vbc36809"
  - "bc36809"
helpviewer_keywords: 
  - "BC36809"
ms.assetid: 560a3370-f24d-4ca3-93b1-39aabe13c238
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les &#233;l&#233;ments descendants XML ne peuvent pas &#234;tre s&#233;lectionn&#233;s &#224; partir du type &#39;type&#39;
Un descendant XML a été référencé pour un objet qui n’est pas de type <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ni `IEnumerable(Of XElement)`. Pour plus d'informations, consultez [XML Descendant Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text"...<childElement>  
```  
  
 **ID d’erreur :** BC36809  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’objet dont vous référencez un élément descendant est fortement typé en tant que <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ou `IEnumerable(Of XElement)`. Voici un exemple :  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem...<child>  
    ```  
  
## Voir aussi  
 [XML Descendant Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-descendant-axis-property)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)