---
title: 'CA1002 : Ne pas exposer de listes génériques'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0612886bf92a4ca6a30e5e15ae1c4a4950d9ddad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236658"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002 : Ne pas exposer de listes génériques

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type contient un membre visible de l’extérieur, qui <xref:System.Collections.Generic.List%601?displayProperty=fullName> est un type, <xref:System.Collections.Generic.List%601> retourne un type, ou dont la <xref:System.Collections.Generic.List%601> signature inclut un paramètre.

## <a name="rule-description"></a>Description de la règle

<xref:System.Collections.Generic.List%601?displayProperty=fullName>est une collection générique conçue pour les performances et non l’héritage. <xref:System.Collections.Generic.List%601>ne contient pas de membres virtuels qui facilitent la modification du comportement d’une classe héritée. Les collections génériques suivantes sont conçues pour l’héritage et doivent être exposées à <xref:System.Collections.Generic.List%601>la place de.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, remplacez le <xref:System.Collections.Generic.List%601?displayProperty=fullName> type par l’une des collections génériques conçues pour l’héritage.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle, sauf si l’assembly qui déclenche cet avertissement n’est pas destiné à être une bibliothèque réutilisable. Par exemple, il serait prudent de supprimer cet avertissement dans une application à performance optimisée où un gain de performances a été obtenu à partir de l’utilisation de listes génériques.

## <a name="related-rules"></a>Règles associées

[CA1005 Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Ne pas déclarer de membres statiques sur des types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006 Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 Utiliser des génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Voir aussi

[Génériques](/dotnet/csharp/programming-guide/generics/index)
