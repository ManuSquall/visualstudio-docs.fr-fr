---
title: "&#39;End&#160;AddHandler&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’une d&#233;claration &#39;AddHandler&#39; correspondante | Microsoft Docs"
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
  - "bc31124"
  - "vbc31124"
helpviewer_keywords: 
  - "BC31124"
ms.assetid: c667fecb-163a-49ca-b416-e1070f4fab1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End&#160;AddHandler&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’une d&#233;claration &#39;AddHandler&#39; correspondante
Une instruction `End AddHandler` s’est produite sans instruction `AddHandler` correspondante.`End AddHandler` doit être précédée d’une instruction `AddHandler` correspondante.  
  
 **ID d’erreur :** BC31124  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’instruction `AddHandler` précédente est valide et correctement orthographiée.  
  
## Voir aussi  
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)