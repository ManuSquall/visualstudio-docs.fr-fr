---
title: "Les param&#232;tres ParamArray doivent &#234;tre d&#233;clar&#233;s &#39;ByVal&#39; | Microsoft Docs"
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
  - "vbc30667"
  - "bc30667"
helpviewer_keywords: 
  - "BC30667"
ms.assetid: 583e231f-a4c9-47aa-ae37-7bac43b0b318
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres ParamArray doivent &#234;tre d&#233;clar&#233;s &#39;ByVal&#39;
Les paramètres `ParamArray` ne peuvent pas utiliser le modificateur `ByRef`.  
  
 **ID d’erreur :** BC30667  
  
### Pour corriger cette erreur  
  
-   Déclarez des paramètres `ParamArray` à l’aide du modificateur `ByVal`.  
  
## Voir aussi  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [ByVal](/dotnet/visual-basic/language-reference/modifiers/byval)