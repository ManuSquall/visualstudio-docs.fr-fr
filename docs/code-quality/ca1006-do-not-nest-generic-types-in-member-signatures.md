---
title: 'CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45ff4831875150df02d04553e75cebcab9a9f572
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236507"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un membre visible de l’extérieur a une signature qui contient un argument de type imbriqué.

## <a name="rule-description"></a>Description de la règle
Un argument de type imbriqué est un argument de type qui est également un type générique. Pour appeler un membre dont la signature contient un argument de type imbriqué, l’utilisateur doit instancier un type générique et passer ce type au constructeur d’un deuxième type générique. La procédure et la syntaxe requises sont complexes et doivent être évitées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, modifiez la conception pour supprimer l’argument de type imbriqué.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle. La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire à l’apprentissage et à l’augmentation du taux d’adoption de nouvelles bibliothèques.

## <a name="example"></a>Exemple
L’exemple suivant montre une méthode qui viole la règle et la syntaxe requise pour appeler la méthode de violation.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA1005 Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Ne pas déclarer de membres statiques sur des types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Ne pas exposer les listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 Utiliser des génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
[Génériques](/dotnet/csharp/programming-guide/generics/index)