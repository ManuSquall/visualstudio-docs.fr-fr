---
title: "La surcharge de m&#233;thodes d&#233;clar&#233;es dans plusieurs interfaces de base n’est pas valide | Microsoft Docs"
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
  - "bc31410"
  - "vbc31410"
helpviewer_keywords: 
  - "BC31410"
ms.assetid: 7d1831c2-837c-4b02-8492-d0fc038fe184
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La surcharge de m&#233;thodes d&#233;clar&#233;es dans plusieurs interfaces de base n’est pas valide
Plusieurs interfaces héritées surchargent implicitement la même méthode.  
  
 **ID d’erreur :** BC31410  
  
### Pour corriger cette erreur  
  
-   Utilisez le modificateur `Shadows` au lieu du modificateur `Overloads`.  
  
## Voir aussi  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)