---
title: "La m&#233;thode ne peut pas comporter simultan&#233;ment des param&#232;tres ParamArray et Optional | Microsoft Docs"
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
  - "vbc30046"
  - "bc30046"
helpviewer_keywords: 
  - "BC30046"
ms.assetid: 41066df8-c9ee-4f67-9f6c-4f62e3abc7be
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode ne peut pas comporter simultan&#233;ment des param&#232;tres ParamArray et Optional
Un argument `ParamArray` est automatiquement facultatif et il doit s’agir du seul argument facultatif dans la déclaration de procédure. Tous les arguments précédents doivent être obligatoires.  
  
 **ID d’erreur :** BC30046  
  
### Pour corriger cette erreur  
  
-   Supprimez les arguments facultatifs dans la déclaration.  
  
## Voir aussi  
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)