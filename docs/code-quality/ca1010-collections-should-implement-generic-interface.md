---
title: 'CA1010 : Les collections doivent implémenter une interface générique'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 066b9d013847f5362ee0dd712002cf8578fb57a6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236440"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010 : Les collections doivent implémenter une interface générique

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type implémente l' <xref:System.Collections.IEnumerable?displayProperty=fullName> interface, mais n’implémente <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> pas l’interface, et l’assembly conteneur cible .net. Cette règle ignore les types qui <xref:System.Collections.IDictionary?displayProperty=fullName>implémentent.

Par défaut, cette règle recherche uniquement les types visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Pour étendre la facilité d’utilisation d’une collection, implémentez l’une des interfaces de collection génériques. La collection peut ensuite être utilisée pour remplir des types de collections génériques, tels que les suivants :

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez l’une des interfaces de collection génériques suivantes :

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle ; Toutefois, l’utilisation de la collection sera plus limitée.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Exemple de violation

L’exemple suivant montre une classe (type référence) qui dérive de la classe non générique `CollectionBase` , qui enfreint cette règle.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Pour corriger une violation de cette règle, effectuez l’une des opérations suivantes :

- Implémentez les interfaces génériques.
- Remplacez la classe de base par un type qui implémente déjà à la fois les interfaces génériques et non génériques, telles `Collection<T>` que la classe.

## <a name="fix-by-base-class-change"></a>Corriger par modification de la classe de base

L’exemple suivant résout la violation en modifiant la classe de base de la collection de la classe `CollectionBase` non générique à la `Collection<T>` classe`Collection(Of T)` générique (dans Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

La modification de la classe de base d’une classe déjà publiée est considérée comme une modification avec rupture apportée aux consommateurs existants.

## <a name="fix-by-interface-implementation"></a>Corriger par l’implémentation de l’interface

L’exemple suivant résout la violation en implémentant ces interfaces `IEnumerable<T>`génériques `ICollection<T>`:, `IList<T>` `IList(Of T)` et`IEnumerable(Of T)`( `ICollection(Of T)`, et dans Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1005 Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000 Ne pas déclarer de membres statiques sur des types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Ne pas exposer les listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003 Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007 Utiliser des génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi

- [Génériques](/dotnet/csharp/programming-guide/generics/index)