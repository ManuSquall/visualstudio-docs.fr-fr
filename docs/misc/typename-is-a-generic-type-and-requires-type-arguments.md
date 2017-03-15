---
title: "&#39;&lt;nom_type&gt;&#39; est un type g&#233;n&#233;rique et requiert des arguments de type | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; est un type g&#233;n&#233;rique et requiert des arguments de type
Une variable, un paramètre de procédure ou un retour de fonction est déclaré comme ayant le type d’une classe ou d’une structure générique, mais la déclaration ne fournit pas d’arguments de type.  
  
 De par sa nature, chaque classe ou structure générique est définie avec au moins un paramètre de type. Quand vous utilisez un type générique pour déclarer une classe ou une structure construite, vous devez fournir un argument de type pour chaque paramètre de type défini par le type générique.  
  
 **ID d’erreur :** BC32076  
  
### Pour corriger cette erreur  
  
-   Ajoutez une liste de types à la déclaration, entourée par des parenthèses et commençant par le mot clé `Of`.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)