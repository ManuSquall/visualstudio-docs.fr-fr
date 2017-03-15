---
title: "&#39;#ElseIf&#39; ne peut pas suivre &#39;#Else&#39; dans un bloc &#39;#If&#39; | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; ne peut pas suivre &#39;#Else&#39; dans un bloc &#39;#If&#39;
Une directive de compilation conditionnelle `#ElseIf` suit une directive `#Else`.`#Else` doit être la dernière directive du bloc conditionnel avant la directive `#End If`.  
  
 **ID d’erreur :** BC32030  
  
### Pour corriger cette erreur  
  
1.  Vérifiez si le `#Else` précédent doit être un `#ElseIf`.  
  
2.  Vérifiez qu’un bloc `#If` précédent est correctement terminé et qu’un nouveau bloc `#If` est commencé.  
  
3.  Si tout le reste est correct, déplacez cette directive `#ElseIf` et son bloc d’instruction correspondant pour qu’il précède le bloc `#Else` .  
  
## Voir aussi  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)