---
title: 'CA1006 : ne pas imbriquer les types génériques dans les signatures de membre | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8063e11d0c3823e265247a0eba2d806819685bf6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655952"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un membre visible de l’extérieur a une signature qui contient un argument de type imbriqué.

## <a name="rule-description"></a>Description de la règle
 Un argument de type imbriqué est un argument de type qui est également un type générique. Pour appeler un membre dont la signature contient un argument de type imbriqué, l'utilisateur doit instancier un type générique et passer ce type au constructeur d'un deuxième type générique. La procédure et la syntaxe requises sont complexes et doivent être évitées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la conception pour supprimer l’argument de type imbriqué.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire à l’apprentissage et à l’augmentation du taux d’adoption de nouvelles bibliothèques.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui viole la règle et la syntaxe requise pour appeler la méthode de violation.

 [!code-csharp[FxCop.Design.NestedGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/cs/FxCop.Design.NestedGenerics.cs#1)]
 [!code-vb[FxCop.Design.NestedGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/vb/FxCop.Design.NestedGenerics.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
 [Génériques](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
