---
title: "Impossible de convertir &#39;type1&#39; en &#39;type2&#39; | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir &#39;type1&#39; en &#39;type2&#39;
Impossible de convertir 'type1' en 'type2'. Vous pouvez utiliser la propriété 'Value' pour obtenir la valeur de chaîne du premier élément de 'parentElement'.  
  
 Une tentative de conversion implicite d’un littéral XML vers un type spécifique a été effectuée. Le littéral XML ne peut pas être implicitement converti vers le type spécifié.  
  
 **ID d’erreur :** BC31193  
  
### Pour corriger cette erreur  
  
-   Utilisez la propriété `Value` du littéral XML pour faire référence à sa valeur comme une `String`. Utilisez la fonction `CType`, une autre fonction de conversion de type, ou la classe <xref:System.Convert> pour effectuer un cast de la valeur vers le type spécifié.  
  
## Voir aussi  
 <xref:System.Convert>   
 [Accessing XML in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/xml/accessing-xml)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)