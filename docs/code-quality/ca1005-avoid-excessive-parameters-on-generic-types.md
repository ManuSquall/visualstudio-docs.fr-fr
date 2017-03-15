---
title: "CA1005&#160;: &#201;viter les param&#232;tres excessifs sur les types g&#233;n&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1005&#160;: &#201;viter les param&#232;tres excessifs sur les types g&#233;n&#233;riques
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type générique visible de l'extérieur contient plus de deux paramètres de type.  
  
## Description de la règle  
 Plus un type générique contient de paramètres de type, plus il est difficile de déterminer et de mémoriser la représentation de chaque paramètre de type.  Cela est généralement évident avec un paramètre de type, comme dans `List<T>`, et dans certains cas avec deux paramètres de type, comme dans `Dictionary<TKey, TValue>`.  Si plus de deux paramètres de type existent, la difficulté devient trop grande pour la plupart des utilisateurs \(par exemple, `TooManyTypeParameters<T, K, V>` en C\# ou `TooManyTypeParameters(Of T, K, V)` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le design afin d'utiliser deux paramètres de type au maximum.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas d'avertissement de cette règle sauf si le design nécessite absolument plus de deux paramètres de type.  La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le délai d'apprentissage nécessaire et augmente le taux d'adoption de nouvelles bibliothèques.  
  
## Règles connexes  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : Ne pas exposer de listes génériques](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)