---
title: 'CA1007 : Utiliser des classes génériques lorsque cela est approprié'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ffb18316b5f009a0f2854c8a158e528f15c92326
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923203"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007 : Utiliser des classes génériques lorsque cela est approprié

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode visible de l’extérieur contient un paramètre de référence <xref:System.Object?displayProperty=fullName>de type, et l’assembly conteneur cible .NET Framework 2,0.

## <a name="rule-description"></a>Description de la règle
Un paramètre de référence est un paramètre modifié à l’aide du `ref` mot`ByRef` clé [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](in). Le type d’argument fourni pour un paramètre de référence doit correspondre exactement au type de paramètre de référence. Pour utiliser un type dérivé du type de paramètre de référence, le type doit d’abord être casté et assigné à une variable du type de paramètre de référence. L’utilisation d’une méthode générique autorise le passage de tous les types, soumis à des contraintes, à la méthode sans cast préalable du type vers le type de paramètre de référence.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, rendez la méthode générique et remplacez <xref:System.Object> le paramètre à l’aide d’un paramètre de type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemples
L’exemple suivant montre une routine d’échange à usage général qui est implémentée en tant que méthodes génériques et non génériques. Notez l’efficacité des chaînes échangées à l’aide de la méthode générique par rapport à la méthode non générique.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA1005 Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Ne pas déclarer de membres statiques sur des types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Ne pas exposer les listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006 Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Voir aussi
[Génériques](/dotnet/csharp/programming-guide/generics/index)