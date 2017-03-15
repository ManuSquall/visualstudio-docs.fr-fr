---
title: "L’argument de type &#39;&lt;nom_argument_type&gt;&#39; doit avoir un constructeur d’instance sans param&#232;tre public pour satisfaire la contrainte &#39;New&#39; pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32083"
  - "BC32083"
helpviewer_keywords: 
  - "BC32083"
ms.assetid: 56bf25f1-375c-4b5d-9969-45eba8b3b66c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’argument de type &#39;&lt;nom_argument_type&gt;&#39; doit avoir un constructeur d’instance sans param&#232;tre public pour satisfaire la contrainte &#39;New&#39; pour le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39;.
Un argument de type fournit un type sans un constructeur sans paramètre accessible à un paramètre de type avec la contrainte [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator).  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Une exigence possible est que l’argument de type doit exposer un constructeur sans paramètre accessible au code de création. Pour spécifier cette exigence, la liste de contraintes inclut la contrainte `New`.  
  
 **ID d’erreur :** BC32083  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le nom de type générique et le nom de type dans l’argument de type sont correctement orthographiés.  
  
2.  Choisissez un type pour l’argument de type qui expose un constructeur sans paramètre accessible. Vous ne pouvez pas appeler ce type générique particulier sauf si vous pouvez fournir un tel argument de type à ce paramètre de type.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Comment : utiliser une classe générique](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)