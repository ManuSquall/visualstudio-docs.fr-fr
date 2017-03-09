---
title: "&#39;End RemoveHandler&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’une instruction &#39;RemoveHandler&#39; correspondante | Microsoft Docs"
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
  - "vbc31125"
  - "bc31125"
helpviewer_keywords: 
  - "BC31125"
ms.assetid: 754a0017-ec55-4d62-a7bd-c84ece058455
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End RemoveHandler&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’une instruction &#39;RemoveHandler&#39; correspondante
Une instruction `End RemoveHandler` s’est produite sans instruction `RemoveHandler` correspondante.`End RemoveHandler` doit être précédé d’une instruction `RemoveHandler` correspondante.  
  
 **ID d’erreur :** BC31125  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’instruction `RemoveHandler` précédente est valide et orthographiée correctement.  
  
## Voir aussi  
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)