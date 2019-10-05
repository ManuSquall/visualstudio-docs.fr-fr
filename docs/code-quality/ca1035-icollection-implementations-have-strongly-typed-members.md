---
title: 'CA1035 : Les implémentations ICollection possèdent des membres fortement typés'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e74daa464a55a543b5eb8c189c9ddf1295301
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236024"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035 : Les implémentations ICollection possèdent des membres fortement typés

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type public ou protégé implémente <xref:System.Collections.ICollection?displayProperty=fullName> , mais ne fournit pas de méthode fortement typée pour. <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> La version fortement typée <xref:System.Collections.ICollection.CopyTo%2A> de doit accepter deux paramètres et ne peut <xref:System.Array?displayProperty=fullName> pas avoir un ou <xref:System.Object?displayProperty=fullName> un tableau de comme premier paramètre.

## <a name="rule-description"></a>Description de la règle
Cette règle requiert <xref:System.Collections.ICollection> que les implémentations fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus <xref:System.Object> d’effectuer un cast d’arguments en type lorsqu’ils utilisent les fonctionnalités fournies par l’interface. Cette règle suppose que le type qui implémente <xref:System.Collections.ICollection> fait cela pour gérer une collection d’instances d’un type qui est plus fort que. <xref:System.Object>

 <xref:System.Collections.ICollection> implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName>. Si les objets de la collection étendent <xref:System.ValueType?displayProperty=fullName>, vous devez fournir un membre fortement typé pour <xref:System.Collections.IEnumerable.GetEnumerator%2A> afin d’éviter la diminution des performances provoquées par la conversion boxing. Cela n’est pas nécessaire lorsque les objets de la collection sont un type référence.

Pour implémenter une version fortement typée d’un membre d’interface, implémentez les membres d’interface explicitement en `InterfaceName.InterfaceMemberName`utilisant des noms <xref:System.Collections.ICollection.CopyTo%2A>sous la forme, tels que. Les membres d’interface explicites utilisent les types de données déclarés par l’interface. Implémentez les membres fortement typés à l’aide du nom de membre <xref:System.Collections.ICollection.CopyTo%2A>d’interface, tel que. Déclarez les membres fortement typés comme publics et déclarez les paramètres et les valeurs de retour comme étant du type fort géré par la collection. Les types forts remplacent les types plus faibles <xref:System.Object> tels <xref:System.Array> que et qui sont déclarés par l’interface.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, implémentez le membre d’interface explicitement (déclarez-le comme <xref:System.Collections.ICollection.CopyTo%2A>). Ajoutez le membre fortement typé public, déclaré comme `CopyTo`, et faites en sorte qu’il prenne un tableau fortement typé en tant que premier paramètre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Supprimez un avertissement de cette règle si vous implémentez une nouvelle collection basée sur un objet, telle qu’une arborescence binaire, où les types qui étendent la nouvelle collection déterminent le type fort. Ces types doivent être conformes à cette règle et exposer des membres fortement typés.

## <a name="example"></a>Exemple
L’exemple suivant illustre la méthode correcte pour implémenter <xref:System.Collections.ICollection>.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA1038 Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039 Les listes sont fortement typées](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>