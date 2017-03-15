---
title: "CA1004&#160;: Les m&#233;thodes g&#233;n&#233;riques doivent fournir un param&#232;tre de type | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1004&#160;: Les m&#233;thodes g&#233;n&#233;riques doivent fournir un param&#232;tre de type
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 La signature de paramètre d'une méthode générique visible de l'extérieur ne contient pas de types correspondant à tous les paramètres de type de la méthode.  
  
## Description de la règle  
 L'inférence désigne la manière dont l'argument de type d'une méthode générique est déterminé par le type d'argument passé à la méthode, au lieu d'utiliser la spécification explicite de l'argument de type.  Pour activer l'inférence, la signature de paramètre d'une méthode générique doit contenir un paramètre du même type que le paramètre de type de la méthode.  Dans ce cas, il n'est pas nécessaire de spécifier l'argument de type.  Lorsque vous utilisez l'inférence pour tous les paramètres de type, la syntaxe d'appel aux méthodes d'instance génériques et non génériques est identique.  Cela simplifie l'utilisation des méthodes génériques.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le design afin que la signature de paramètre contienne un type identique pour chacun des paramètres de type de la méthode.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le délai d'apprentissage nécessaire et augmente le taux d'adoption de nouvelles bibliothèques.  
  
## Exemple  
 L'exemple suivant illustre la syntaxe d'appel à deux méthodes génériques.  L'argument de type pour `InferredTypeArgument` est déduit, et l'argument de type pour `NotInferredTypeArgument` doit être spécifié explicitement.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## Règles connexes  
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : Ne pas exposer de listes génériques](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)