---
title: "&#39;Loop&#39; doit &#234;tre pr&#233;c&#233;d&#233;e d’une instruction &#39;Do&#39; correspondante | Microsoft Docs"
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
  - "vbc30091"
  - "bc30091"
helpviewer_keywords: 
  - "BC30091"
ms.assetid: 05f47b2f-4eaa-4911-981e-3fce737d249f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Loop&#39; doit &#234;tre pr&#233;c&#233;d&#233;e d’une instruction &#39;Do&#39; correspondante
Une instruction `Loop` ne possède pas d’instruction `Do` correspondante.`Loop` doit être précédée d’une instruction `Do` correspondante.  
  
 **ID d’erreur :** BC30091  
  
### Pour corriger cette erreur  
  
1.  Si cette boucle `Do` fait partie d’un ensemble de boucles `Do` imbriquées, vérifiez que chaque boucle est correctement terminée.  
  
2.  Vérifiez que les autres structures de contrôle de la boucle `Do` ont été correctement terminées.  
  
3.  Vérifiez que cette boucle `Do` est correctement mise en forme.  
  
## Voir aussi  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)