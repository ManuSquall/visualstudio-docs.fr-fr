---
title: "La balise de commentaire XML &#39;returns&#39; n’est pas autoris&#233;e pour un &#233;l&#233;ment de langage &#39;declare sub&#39; | Microsoft Docs"
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
  - "bc42315"
  - "vbc42315"
helpviewer_keywords: 
  - "BC42315"
ms.assetid: 55ba3e8a-ba7f-42e3-a4a7-b22844e72564
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La balise de commentaire XML &#39;returns&#39; n’est pas autoris&#233;e pour un &#233;l&#233;ment de langage &#39;declare sub&#39;
La balise de commentaire XML 'returns' n'est pas autorisée pour un élément de langage 'declare sub'. Le commentaire XML sera ignoré.  
  
 Un commentaire XML pour une déclaration `Declare Sub` ne peut pas contenir de balise `<`returns`>`.  
  
 **ID d’erreur :** BC42315  
  
### Pour corriger cette erreur  
  
-   Supprimez la balise `<`returns`>` non prise en charge.  
  
## Voir aussi  
 [\<returns\>](../Topic/%3Creturns%3E%20\(Visual%20Basic\).md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documenting Your Code with XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)