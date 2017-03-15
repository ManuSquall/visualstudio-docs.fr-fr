---
title: "La m&#233;thode &#39;MustOverride&#39; &#39;&lt;nom_m&#233;thode&gt;&#39; ne peut pas &#234;tre appel&#233;e par &#39;MyClass&#39; | Microsoft Docs"
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
  - "bc30614"
  - "vbc30614"
helpviewer_keywords: 
  - "BC30614"
ms.assetid: fc57af41-1552-46d1-9727-341f1835e661
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;MustOverride&#39; &#39;&lt;nom_m&#233;thode&gt;&#39; ne peut pas &#234;tre appel&#233;e par &#39;MyClass&#39;
`MyClass` équivaut à `Me`, mais tous les appels de méthode sur celui\-ci sont traités comme si la méthode invoquée était `NotOverridable`.  
  
 **ID d’erreur :** BC30614  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur `MustOverride` ou déclarez la méthode dans une classe de base, héritez et substituez cette classe.  
  
## Voir aussi  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)