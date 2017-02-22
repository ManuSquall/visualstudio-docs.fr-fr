---
title: "CA1006&#160;: Ne pas imbriquer les types g&#233;n&#233;riques dans les signatures de membre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006&#160;: Ne pas imbriquer les types g&#233;n&#233;riques dans les signatures de membre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un membre visible de l'extérieur a une signature qui contient un argument de type imbriqué.  
  
## Description de la règle  
 Un argument de type imbriqué est un argument de type qui est également un type générique.  Pour appeler un membre dont la signature contient un argument de type imbriqué, l'utilisateur doit instancier un type générique et passer ce type au constructeur d'un deuxième type générique.  La procédure et la syntaxe requises sont complexes et doivent être évitées.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le design afin de supprimer l'argument de type imbriqué.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le délai d'apprentissage nécessaire et augmente le taux d'adoption de nouvelles bibliothèques.  
  
## Exemple  
 L'exemple suivant présente une méthode qui viole la règle et la syntaxe requises pour appeler la méthode en violation.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## Règles connexes  
 [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : Ne pas exposer de listes génériques](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007 : Utiliser des classes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)