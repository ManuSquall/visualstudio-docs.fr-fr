---
title: "L’op&#233;rande &#39;SyncLock&#39; ne peut pas &#234;tre de type &#39;&lt;nom_type&gt;&#39;, car &#39;&lt;nom_type&gt;&#39; n’est pas un type r&#233;f&#233;rence | Microsoft Docs"
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
  - "vbc30582"
  - "bc30582"
helpviewer_keywords: 
  - "BC30582"
ms.assetid: 953aecf2-629a-4272-94bd-abf88f785e63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rande &#39;SyncLock&#39; ne peut pas &#234;tre de type &#39;&lt;nom_type&gt;&#39;, car &#39;&lt;nom_type&gt;&#39; n’est pas un type r&#233;f&#233;rence
L’instruction `SyncLock` autorise la synchronisation d’instructions sur une seule expression en veillant à ce que plusieurs threads n’exécutent pas les mêmes instructions en même temps. Le type d’expression dans une instruction `SyncLock` doit être un type référence, par exemple une classe, un module, une interface, un tableau ou un délégué.  
  
 **ID d’erreur :** BC30582  
  
### Pour corriger cette erreur  
  
-   Remplacez le type par un type référence approprié.  
  
## Voir aussi  
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)   
 [NOT IN BUILD : Multithreading en Visual Basic](http://msdn.microsoft.com/fr-fr/c731a50c-09c1-4468-9646-54c86b75d269)