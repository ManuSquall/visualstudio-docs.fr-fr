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
ms.openlocfilehash: c71912fdd70226e1b4be3c14be7c4e0bac26259d
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57871900"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010 : Les collections doivent implémenter une interface générique

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type implémente le <xref:System.Collections.IEnumerable?displayProperty=fullName> interface mais n’implémente pas le <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface et .NET cibles assembly conteneur. Cette règle ignore les types qui implémentent <xref:System.Collections.IDictionary?displayProperty=fullName>.

Par défaut, cette règle examine uniquement les types visibles de l’extérieur, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Pour étendre la facilité d’utilisation d’une collection, implémentez l’une des interfaces de collection génériques. Puis la collection peut être utilisée pour remplir des types de collections génériques telles que les éléments suivants :

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez l’une des interfaces de collection génériques suivantes :

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle ; Toutefois, l’utilisation de la collection sera plus limitée.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.ca1010.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Exemple de violation

L’exemple suivant montre une classe qui dérive de la non générique (type référence) `CollectionBase` (classe), ce qui enfreint cette règle.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Pour corriger une violation de cette règle, effectuez l’une des opérations suivantes :

- Implémenter les interfaces génériques.
- Modifier la classe de base à un type qui implémente déjà les interfaces génériques et non génériques, tels que le `Collection<T>` classe.

## <a name="fix-by-base-class-change"></a>Résoudre par modification de la classe de base

L’exemple suivant résout la violation en modifiant la classe de base de la collection non générique `CollectionBase` générique `Collection<T>` (`Collection(Of T)` en Visual Basic) classe.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Modification de la classe de base d’une classe déjà publiée d’est considéré comme une modification avec rupture pour les utilisateurs existants.

## <a name="fix-by-interface-implementation"></a>Résoudre par implémentation d’interface

L’exemple suivant résout la violation en implémentant ces interfaces génériques : `IEnumerable<T>`, `ICollection<T>`, et `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, et `IList(Of T)` en Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Règles associées

- [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003 : Utiliser des instances du Gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007 : Utiliser des classes génériques le cas échéant](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi

- [Génériques](/dotnet/csharp/programming-guide/generics/index)