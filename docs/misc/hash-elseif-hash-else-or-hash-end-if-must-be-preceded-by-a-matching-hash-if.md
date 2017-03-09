---
title: "&#39;#ElseIf&#39;, &#39;#Else&#39; ou &#39;#End If&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#If&#39; correspondant | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39;, &#39;#Else&#39; ou &#39;#End If&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;#If&#39; correspondant
`#ElseIf`, `#Else` et `#End If` sont des directives de compilation conditionnelle.`#ElseIf`, `#Else` ou `#End If` n’est pas précédé d’une directive `#If` correspondante.  
  
 **ID d’erreur :** BC30013  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la directive `#If` prévue n’est pas séparée de la clause en question par un bloc de compilation conditionnelle intervenant ou une directive `#End If` mal placée.  
  
    > [!NOTE]
    >  Seule une directive `#Else` étant autorisée dans chaque bloc `#If`, deux directives `#Else` successives provoquent cette erreur.  
  
2.  Vérifiez que le caractère de début `#` est présent dans une directive `#If` précédente.  
  
3.  Si tout le reste est en ordre, ajoutez une directive `#If` au début du bloc de compilation conditionnelle.  
  
## Voir aussi  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)