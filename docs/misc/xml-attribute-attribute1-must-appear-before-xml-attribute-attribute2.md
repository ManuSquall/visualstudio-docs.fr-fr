---
title: "L’attribut XML &#39;attribut1&#39; doit appara&#238;tre avant l’attribut XML &#39;attribut2&#39; | Microsoft Docs"
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
  - "bc31157"
  - "vbc31157"
helpviewer_keywords: 
  - "BC31157"
ms.assetid: d8d8769e-533d-454e-b145-99955ce45cc5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut XML &#39;attribut1&#39; doit appara&#238;tre avant l’attribut XML &#39;attribut2&#39;
Les attributs dans un littéral de document XML sont spécifiés dans un ordre non valide. L’ordre valide des attributs pour un littéral de document XML est basé sur la spécification XML 1.0. Par exemple, l’attribut `encoding` d’un littéral de document XML doit suivre immédiatement l’attribut `version`.  
  
 **ID d’erreur :** BC31157  
  
### Pour corriger cette erreur  
  
-   Mettez à jour l’ordre des attributs pour le littéral de document XML en suivant les recommandations fournies dans la spécification XML 1.0.  
  
## Voir aussi  
 [XML Literals and the XML 1.0 Specification](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification)   
 [XML Document Literal](/dotnet/visual-basic/language-reference/xml-literals/xml-document-literal)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)