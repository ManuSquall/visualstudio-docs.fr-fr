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
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238103"
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

Un type sérialisable est un type qui est marqué avec l' <xref:System.SerializableAttribute?displayProperty=fullName> attribut. Quand le type est sérialisé, une <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> exception est levée si le type contient un champ d’instance d’un type qui n’est pas sérialisable *et* n’implémente <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> pas l’interface.

> [!TIP]
> CA2235 ne se déclenche pas pour les champs d’instance de <xref:System.Runtime.Serialization.ISerializable> types qui implémentent, car ils fournissent leur propre logique de sérialisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appliquez l' <xref:System.NonSerializedAttribute?displayProperty=fullName> attribut au champ qui n’est pas sérialisable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez uniquement un avertissement de cette règle si <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> un type déclaré qui autorise les instances du champ à être sérialisé et désérialisé.

## <a name="example"></a>Exemple

L’exemple suivant illustre deux types : un qui enfreint la règle et un autre qui répond à la règle.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Notes

La règle CA2235 n’analyse pas les types qui <xref:System.Runtime.Serialization.ISerializable> implémentent l’interface (sauf s’ils sont <xref:System.SerializableAttribute> également marqués avec l’attribut). En effet, la [règle CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) recommande déjà de marquer les types <xref:System.Runtime.Serialization.ISerializable> qui implémentent <xref:System.SerializableAttribute> l’interface avec l’attribut.

## <a name="related-rules"></a>Règles associées

- [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236 Appeler les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238 Implémenter les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239 Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240 Implémenter ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120 Sécuriser les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)