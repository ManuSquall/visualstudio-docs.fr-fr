---
title: 'CA1005 : Éviter les paramètres excessifs sur les types génériques'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc94a04d708315cc143afd1556cb8a2f0072e91
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923301"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005 : Éviter les paramètres excessifs sur les types génériques

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type générique visible de l’extérieur a plus de deux paramètres de type.

## <a name="rule-description"></a>Description de la règle
Plus un type générique contient de paramètres de type, plus il est difficile de déterminer et de mémoriser la représentation de chaque paramètre de type. Elle est généralement évidente avec un paramètre de type, comme `List<T>`dans, et dans certains cas, avec deux paramètres de type `Dictionary<TKey, TValue>`, comme dans. S’il existe plus de deux paramètres de type, la difficulté devient trop importante pour la plupart des utilisateurs `TooManyTypeParameters<T, K, V>` ( C# par `TooManyTypeParameters(Of T, K, V)` exemple [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dans ou dans).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, modifiez la conception de sorte qu’elle n’utilise pas plus de deux paramètres de type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un avertissement de cette règle, sauf si la conception requiert absolument plus de deux paramètres de type. La fourniture de génériques dans une syntaxe facile à comprendre et à utiliser réduit le temps nécessaire à l’apprentissage et à l’augmentation du taux d’adoption de nouvelles bibliothèques.

## <a name="related-rules"></a>Règles associées
[CA1010 Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Ne pas déclarer de membres statiques sur des types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Ne pas exposer les listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006 Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 Utiliser des génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi
[Génériques](/dotnet/csharp/programming-guide/generics/index)