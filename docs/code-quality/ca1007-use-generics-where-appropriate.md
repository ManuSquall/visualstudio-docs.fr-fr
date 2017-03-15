---
title: "CA1007&#160;: Utiliser des classes g&#233;n&#233;riques lorsque cela est appropri&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1007&#160;: Utiliser des classes g&#233;n&#233;riques lorsque cela est appropri&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode visible de l'extérieur contient un paramètre de référence de type <xref:System.Object?displayProperty=fullName>, et l'assembly conteneur vise le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Description de la règle  
 Un paramètre de référence est un paramètre qui est modifié à l'aide du mot clé `ref` \(`ByRef` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Le type d'argument fourni pour un paramètre de référence doit correspondre exactement au type de paramètre de référence.  Pour utiliser un type dérivé du type de paramètre de référence, vous devez d'abord effectuer un cast du type et l'assigner à une variable du type de paramètre de référence.  L'utilisation d'une méthode générique autorise le passage de tous les types, soumis à des contraintes, dans la méthode sans cast préalable du type vers le type de paramètre de référence.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez la méthode générique et remplacez le paramètre <xref:System.Object> par un paramètre de type.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente une routine de permutation à usage général implémentée comme des méthodes génériques et non génériques.  Notez l'efficacité de la permutation des chaînes à l'aide de la méthode générique par rapport à la méthode non générique.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## Règles connexes  
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : Ne pas exposer de listes génériques](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)