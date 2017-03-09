---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une fonction &#39;Declare&#39; | Microsoft Docs"
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
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; &#224; une fonction &#39;Declare&#39;
L’attribut `DllImportAttribute` a été appliqué à une fonction `Declare`. Cet attribut peut uniquement être utilisé avec un `Function` ou `Sub` vide.  
  
 **ID d’erreur :** BC31523  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’attribut `DllImportAttribute` de l’instruction `Declare`.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)