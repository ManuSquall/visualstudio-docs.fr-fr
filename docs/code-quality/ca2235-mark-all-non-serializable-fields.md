---
title: 'CA2235 : Marquez tous les champs non sérialisés'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ebfa5e9b90951acf59c8214941b93adae76d06e
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177390"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235 : Marquez tous les champs non sérialisés

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.

## <a name="rule-description"></a>Description de la règle

Un type sérialisable est celui qui est marqué avec le <xref:System.SerializableAttribute?displayProperty=fullName> attribut. Lorsque le type est sérialisé, une <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> exception est levée si le type contient un champ d’instance d’un type qui n’est pas sérialisable *et* n’implémente pas le <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface.

> [!TIP]
> CA2235 ne se déclenche pas par exemple les champs de types qui implémentent <xref:System.Runtime.Serialization.ISerializable> , car ils fournissent leur propre logique de sérialisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appliquez le <xref:System.NonSerializedAttribute?displayProperty=fullName> attribut au champ qui n’est pas sérialisable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez uniquement un avertissement de cette règle si un <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> type est déclaré qui permet aux instances du champ à être sérialisées et désérialisées.

## <a name="example"></a>Exemple

L’exemple suivant montre deux types : un qui enfreint la règle et une autre qui satisfait la règle.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Notes

Règle CA2235 n’analyse pas les types qui implémentent le <xref:System.Runtime.Serialization.ISerializable> interface (sauf s’ils sont également marqués avec le <xref:System.SerializableAttribute> attribut). Il s’agit, car [règle CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) déjà recommande de marquer les types qui implémentent le <xref:System.Runtime.Serialization.ISerializable> créent une interface avec le <xref:System.SerializableAttribute> attribut.

## <a name="related-rules"></a>Règles associées

- [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236 : Appeler des méthodes de classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238 : Implémentez les méthodes de sérialisation](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120 : Constructeurs de sérialisation sécurisé](../code-quality/ca2120-secure-serialization-constructors.md)