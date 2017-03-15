---
title: "Le bloc&#39;#If&#39; doit se terminer par un &#39;#End If&#39; correspondant | Microsoft Docs"
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
  - "vbc30012"
  - "bc30012"
helpviewer_keywords: 
  - "BC30012"
ms.assetid: 9d51f3be-d2c3-4918-a36d-0d9e9763e47b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le bloc&#39;#If&#39; doit se terminer par un &#39;#End If&#39; correspondant
`#If` est une directive de compilation conditionnelle. Un bloc `#If` n’est pas terminé par une directive `#End If`.  
  
 **ID d’erreur :** BC30012  
  
### Pour corriger cette erreur  
  
-   Ajoutez une directive `#End If` à la fin du bloc de compilation conditionnelle.  
  
## Voir aussi  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)