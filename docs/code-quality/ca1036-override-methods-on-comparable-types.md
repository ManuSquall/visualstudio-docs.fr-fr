---
title: 'CA1036 : Substituer les méthodes sur les types Comparable'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868870"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036 : Substituer les méthodes sur les types Comparable

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type implémente le <xref:System.IComparable?displayProperty=fullName> interface et ne se substitue pas <xref:System.Object.Equals%2A?displayProperty=fullName> ou ne surcharge pas l’opérateur spécifique à la langue pour l’égalité, inégalité, moins-à ou supérieur-que. La règle ne signale pas d’une violation si le type hérite uniquement une implémentation de l’interface.

Par défaut, cette règle examine uniquement les types publics et protégés, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Les types qui définissent un ordre de tri personnalisé implémentent la <xref:System.IComparable> interface. Le <xref:System.IComparable.CompareTo%2A> méthode retourne une valeur entière qui indique l’ordre de tri correct pour les deux instances du type. Cette règle identifie les types de définir un ordre de tri. Définition d’un ordre de tri implique que la signification ordinaire d’égalité, inégalité, less- et inférieur-que ne s’appliquent pas. Lorsque vous fournissez une implémentation de <xref:System.IComparable>, vous devez généralement également substituer <xref:System.Object.Equals%2A> afin qu’il retourne des valeurs qui sont cohérents avec <xref:System.IComparable.CompareTo%2A>. Si vous substituez <xref:System.Object.Equals%2A> et codez dans un langage qui prend en charge les surcharges d’opérateur, vous devez également fournir des opérateurs sont cohérents avec <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, substituez <xref:System.Object.Equals%2A>. Si votre langage de programmation prend en charge la surcharge d’opérateur, fournissez les opérateurs suivants :

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

En c#, les jetons qui sont utilisés pour représenter ces opérateurs sont les suivantes :

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de règle CA1036 quand la violation est due à l’absence d’opérateurs et votre langage de programmation ne prend pas en charge la surcharge d’opérateur, comme c’est le cas avec Visual Basic. Si vous déterminez que les opérateurs de mise en œuvre n’est pas pertinent dans le contexte de votre application, il est également possible de supprimer un avertissement de cette règle quand elle se déclenche sur les opérateurs d’égalité autres qu’op_Equality sans. Toutefois, vous devez toujours remplacer op_Equality et l’opérateur == si vous substituez <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="examples"></a>Exemples

Le code suivant contient un type qui implémente correctement <xref:System.IComparable>. Commentaires de code identifient les méthodes qui satisfont différentes règles liées à <xref:System.Object.Equals%2A> et <xref:System.IComparable> interface.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Le code d’application suivante teste le comportement de la <xref:System.IComparable> implémentation mentionnée précédemment.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators)