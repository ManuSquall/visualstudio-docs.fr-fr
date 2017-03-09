---
title: "&#39;Next&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;For&#39; correspondant | Microsoft Docs"
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
  - "vbc30092"
  - "bc30092"
helpviewer_keywords: 
  - "BC30092"
ms.assetid: 4bf49bb2-c69b-443d-aa58-cb40fcfb1370
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;For&#39; correspondant
Une instruction `Next` ne possède pas d’instruction `For` ou `For Each` correspondante.`Next` doit être précédé d’une instruction `For` ou `For Each` correspondante.  
  
 **ID d’erreur :** BC30092  
  
### Pour corriger cette erreur  
  
1.  Si cette boucle `For` fait partie d’un ensemble de boucles `For` imbriquées, vérifiez que chaque boucle est correctement terminée.  
  
2.  Vérifiez que les autres structures de contrôle dans la boucle `For` sont terminées correctement.  
  
3.  Vérifiez que cette boucle `For` est correctement mise en forme.  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [For Each...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)