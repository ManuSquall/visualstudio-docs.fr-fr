---
title: "Les &#233;l&#233;ments XML ne peuvent pas &#234;tre s&#233;lectionn&#233;s &#224; partir du type &#39;type&#39; | Microsoft Docs"
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
  - "vbc36807"
  - "bc36807"
helpviewer_keywords: 
  - "BC36807"
ms.assetid: 01c19899-2b44-41e9-a99c-35edfa0deaf1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les &#233;l&#233;ments XML ne peuvent pas &#234;tre s&#233;lectionn&#233;s &#224; partir du type &#39;type&#39;
Un élément enfant XML a été référencé pour un objet qui n’est pas du type <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ou `IEnumerable(Of XElement)`. Pour plus d'informations, consultez [XML Child Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property).  
  
```vb#  
' Generates an error. Dim var = "sample text".<child>  
```  
  
 **ID d’erreur :** BC36807  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que l’objet dont vous référencez un attribut est fortement typé en tant que <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ou `IEnumerable(Of XElement)`. Voici un exemple :  
  
    ```vb#  
    Dim elem As XElement = <root> <child /> </root> Dim var = elem.<child>  
    ```  
  
## Voir aussi  
 [XML Child Axis Property](/dotnet/visual-basic/language-reference/xml-axis/xml-child-axis-property)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)