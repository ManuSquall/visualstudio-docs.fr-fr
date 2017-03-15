---
title: "Option Strict On interdit le passage du type &#39;&lt;nom_type1&gt;&#39; au type &#39;&lt;nom_type2&gt;&#39; lors de la recopie de la valeur du param&#232;tre &#39;ByRef&#39; &#39;&lt;nom_param&#232;tre&gt;&#39; dans l’argument correspondant | Microsoft Docs"
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
  - "bc32029"
  - "vbc32029"
helpviewer_keywords: 
  - "BC32029"
ms.assetid: fc9ae5d2-b506-47cf-a50c-116fda5ed206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On interdit le passage du type &#39;&lt;nom_type1&gt;&#39; au type &#39;&lt;nom_type2&gt;&#39; lors de la recopie de la valeur du param&#232;tre &#39;ByRef&#39; &#39;&lt;nom_param&#232;tre&gt;&#39; dans l’argument correspondant
Un appel de procédure fournit un argument `ByRef` avec un type de données qui s’étend au type déclaré de l’argument, et `Option Strict` a la valeur `On`. La conversion étendue est autorisée quand l’argument est passé à la procédure. Toutefois, quand la procédure modifie le contenu de l’argument de variable dans le code appelant, la conversion inverse est restrictive. Les conversions restrictives ne sont pas autorisées avec `Option Strict On`.  
  
 **ID d’erreur :** BC32029  
  
### Pour corriger cette erreur  
  
-   Spécifiez chaque argument `ByRef` dans l’appel de procédure avec le même type de données que le type déclaré ou définissez `Option Strict Off`.  
  
## Voir aussi  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)