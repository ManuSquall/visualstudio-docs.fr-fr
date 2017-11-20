---
title: "CA1006 : Ne s’imbriquent pas de types génériques dans les signatures de membre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2ec28ce2cfe1e8c0de622a0f35d37ddd82e1be7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre
|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un membre extérieurement visible a une signature qui contient un argument de type imbriqué.  
  
## <a name="rule-description"></a>Description de la règle  
 Un argument de type imbriqué est un argument de type qui est également un type générique. Pour appeler un membre dont la signature contient un argument de type imbriqué, l'utilisateur doit instancier un type générique et passer ce type au constructeur d'un deuxième type générique. La procédure et la syntaxe requises sont complexes et doivent être évitées.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le design pour supprimer l’argument de type imbriqué.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire pour en savoir plus et augmente le taux d’adoption de nouvelles bibliothèques.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui enfreint la règle et la syntaxe qui est requis pour appeler la méthode en violation.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](/dotnet/csharp/programming-guide/generics/index)