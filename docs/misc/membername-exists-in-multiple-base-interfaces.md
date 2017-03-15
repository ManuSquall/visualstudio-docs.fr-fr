---
title: "&#39;&lt;nom_membre&gt;&#39; existe dans plusieurs interfaces de base | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_membre&gt;&#39; existe dans plusieurs interfaces de base
'\<nom\_membre\>' existe dans plusieurs interfaces de base. Utilisez le nom de l’interface qui déclare '\<nom\_membre\>' dans la clause 'Implements' au lieu du nom de l’interface dérivée.  
  
 Cette interface hérite des membres portant le même nom de plusieurs interfaces, créant ainsi une ambiguïté.  
  
 **ID d’erreur :** BC31040  
  
### Pour corriger cette erreur  
  
-   Utilisez le nom d’interface de définition dans les clauses `Implements` au lieu du nom de l’interface dérivée.  
  
## Voir aussi  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)