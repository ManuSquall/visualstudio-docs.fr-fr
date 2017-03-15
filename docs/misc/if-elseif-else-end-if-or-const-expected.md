---
title: "&#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; ou &#39;Const&#39; attendu | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39;, &#39;ElseIf&#39;, &#39;Else&#39;, &#39;End If&#39; ou &#39;Const&#39; attendu
Une ligne source commence par un caractère `#`, mais une directive de compilation conditionnelle valide ne suit pas immédiatement le caractère `#`. Parmi les directives valides, citons `#Const`, `#ExternalSource`, `#If`, `#Else`, `#ElseIf`, `#End If` et `#Region`.  
  
 **ID d’erreur :** BC30248  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la directive de compilation conditionnelle est correctement orthographiée.  
  
2.  Vérifiez qu’il n’existe pas d’espace intermédiaire entre le caractère `#` et la directive.  
  
3.  Supprimez le caractère `#` ou ajoutez une directive valide immédiatement après celui\-ci.  
  
## Voir aussi  
 [Directives](/dotnet/visual-basic/language-reference/directives/directives)