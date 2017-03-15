---
title: "Une m&#233;thode ne peut pas contenir &#224; la fois une instruction &#39;Try&#39; et une instruction &#39;On Error&#39; ou &#39;Resume&#39; | Microsoft Docs"
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
  - "vbc30544"
  - "bc30544"
helpviewer_keywords: 
  - "BC30544"
ms.assetid: 1e75d5fe-9a6b-43c2-9749-1f2d7ce5b10d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une m&#233;thode ne peut pas contenir &#224; la fois une instruction &#39;Try&#39; et une instruction &#39;On Error&#39; ou &#39;Resume&#39;
Vous avez associé une instruction `Try` à `On Error` ou `Resume`.  
  
 **ID d’erreur :** BC30544  
  
### Pour corriger cette erreur  
  
1.  Supprimez `On Error` ou `Resume`.  
  
## Voir aussi  
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)