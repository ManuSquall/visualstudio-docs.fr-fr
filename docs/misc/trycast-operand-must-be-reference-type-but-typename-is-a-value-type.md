---
title: "L’op&#233;rande &#39;TryCast&#39; doit &#234;tre un type r&#233;f&#233;rence, mais &#39;&lt;nom_type&gt;&#39; est un type valeur | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’op&#233;rande &#39;TryCast&#39; doit &#234;tre un type r&#233;f&#233;rence, mais &#39;&lt;nom_type&gt;&#39; est un type valeur
L’opérateur `TryCast` est utilisé avec un type valeur pour au moins un des arguments.  
  
 `TryCast` vérifie s’il existe une relation d’héritage ou d’implémentation entre les deux arguments. Ainsi, seuls les types référence sont autorisés pour les arguments. Pour plus d'informations, consultez [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types).  
  
 **ID d’erreur :** BC30792  
  
### Pour corriger cette erreur  
  
-   Utilisez `DirectCast` ou `CType` pour effectuer la conversion. Tous deux acceptent les types valeur.  
  
## Voir aussi  
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [CType, fonction](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)