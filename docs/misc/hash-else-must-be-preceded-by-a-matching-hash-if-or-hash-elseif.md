---
title: "&#39;#Else&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#If&#39; ou &#39;#ElseIf&#39; correspondant | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Else&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#If&#39; ou &#39;#ElseIf&#39; correspondant
`#Else` est une directive de compilation conditionnelle. Une directive `#Else` n’est pas précédée d’une directive `#If` ou `#ElseIf` correspondant.  
  
 **ID d’erreur :** BC30028  
  
### Pour corriger cette erreur  
  
1.  Vérifiez qu’une directive `#If` ou `#ElseIf` précédente n’est pas séparée de cette directive `#Else` par un bloc de compilation conditionnelle existant ou mal placé `#End If`.  
  
2.  Vérifiez que la directive `#Else` est précédée d’une autre directive `#Else`. Si c’est le cas, supprimez la directive `#Else` ou remplacez\-la par une directive `#ElseIf`.  
  
3.  Si tout le reste est en ordre, ajoutez une directive `#If` au début du bloc de compilation conditionnelle.  
  
## Voir aussi  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)