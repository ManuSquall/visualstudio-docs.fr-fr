---
title: 'CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fafa4782762e18f1ced8c7f929720e995986ac7a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546867"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type valeur se substitue <xref:System.Object.Equals%2A?displayProperty=fullName> à, mais n’implémente pas l’opérateur d’égalité.

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Dans la plupart des langages de programmation, il n’y a pas d’implémentation par défaut de l’opérateur d’égalité (= =) pour les types valeur. Si votre langage de programmation prend en charge les surcharges d’opérateur, vous devez envisager d’implémenter l’opérateur d’égalité. Son comportement doit être identique à celui de <xref:System.Object.Equals%2A>.

Vous ne pouvez pas utiliser l’opérateur d’égalité par défaut dans une implémentation surchargée de l’opérateur d’égalité. Cela entraîne un dépassement de capacité de la pile. Pour implémenter l’opérateur d’égalité, utilisez la méthode Object. Equals dans votre implémentation. Par exemple :

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez l’opérateur d’égalité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle; Toutefois, nous vous recommandons de fournir l’opérateur d’égalité, si possible.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.ca2231.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (utilisation). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant définit un type qui viole cette règle:

[!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1046 Ne pas surcharger l’opérateur égal à sur les types référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225 Les surcharges d’opérateur ont des alternatives nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2226 Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224 Remplacer Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218 Substituez GetHashCode lors du remplacement d’égal](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Object.Equals%2A?displayProperty=fullName>