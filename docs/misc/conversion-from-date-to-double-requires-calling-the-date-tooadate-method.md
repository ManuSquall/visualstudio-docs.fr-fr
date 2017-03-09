---
title: "Pour convertir &#39;Date&#39; en &#39;Double&#39;, vous devez appeler la m&#233;thode &#39;Date.ToOADate&#39; | Microsoft Docs"
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
  - "bc30532"
  - "vbc30532"
helpviewer_keywords: 
  - "BC30532"
ms.assetid: 8171ce21-e4f6-4e75-b7e8-32baf78a40eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Pour convertir &#39;Date&#39; en &#39;Double&#39;, vous devez appeler la m&#233;thode &#39;Date.ToOADate&#39;
Vous avez tenté d’effectuer un cast d’une valeur `Date` en une valeur `Double`, ce qui ne peut pas être fait sans utiliser la méthode <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>.  
  
 **ID d’erreur :** BC30532  
  
### Pour corriger cette erreur  
  
-   Utilisez la méthode <xref:System.DateTime.ToOADate%2A?displayProperty=fullName> pour convertir la valeur.  
  
## Voir aussi  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)