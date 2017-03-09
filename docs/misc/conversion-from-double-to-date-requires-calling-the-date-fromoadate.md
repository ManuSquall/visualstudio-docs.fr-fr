---
title: "Pour convertir &#39;Double&#39; en &#39;Date&#39;, vous devez appeler la m&#233;thode &#39;Date.FromOADate&#39; | Microsoft Docs"
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
  - "vbc30533"
  - "bc30533"
helpviewer_keywords: 
  - "BC30533"
ms.assetid: afcfd115-4614-4b0b-ad09-76af8dba2ed5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Pour convertir &#39;Double&#39; en &#39;Date&#39;, vous devez appeler la m&#233;thode &#39;Date.FromOADate&#39;
Vous avez tenté d’effectuer une conversion de type \(transtypage\) d’une valeur `Date` en valeur `Double`, ce qui n’est pas possible sans utiliser la méthode <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>.  
  
 **ID d’erreur :** BC30533  
  
### Pour corriger cette erreur  
  
-   Utilisez la méthode <xref:System.DateTime.FromOADate%2A> pour convertir la valeur.  
  
## Voir aussi  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)