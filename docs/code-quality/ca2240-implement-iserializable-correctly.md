---
title: 'CA2240 : Implémentez ISerializable comme il se doit'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9ef3e012b3a818c60be23278fe622a40330f3b43
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935396"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240 : Implémentez ISerializable comme il se doit

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type extérieurement visible ne peut être assigné à la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface et une des conditions suivantes est vraie :

- Le type hérite mais ne remplace pas le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (méthode) et le type déclare des champs d’instance qui ne sont pas marqués avec le <xref:System.NonSerializedAttribute?displayProperty=fullName> attribut.

- Le type n’est pas scellé et le type implémente une <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode qui n’est pas extérieurement visible et substituable.

## <a name="rule-description"></a>Description de la règle
 Champs d’instance qui sont déclarés dans un type qui hérite du <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface ne sont pas automatiquement inclus dans le processus de sérialisation. Pour inclure les champs, le type doit implémenter la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> (méthode) et le constructeur de sérialisation. Si les champs ne doivent pas être sérialisées, appliquez le <xref:System.NonSerializedAttribute> aux champs pour indiquer explicitement la décision d’attribut.

 Dans les types qui ne sont pas sealed, les implémentations de la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode doit être visible de l’extérieur. Par conséquent, la méthode peut être appelée par des types dérivés et est substituable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode visible et substituable et assurez-vous que tous les champs d’instance sont inclus dans le processus de sérialisation ou sont marqués explicitement avec le <xref:System.NonSerializedAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux types sérialisables qui enfreignent la règle.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Exemple
 L’exemple suivant résout les deux violations ci-dessus en fournissant une implémentation substituable de <xref:System.Runtime.Serialization.ISerializable.GetObjectData> sur la classe Book et en fournissant une implémentation de `GetObjectData` sur la classe de bibliothèque.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Règles associées

- [CA2236 : Appeler des méthodes de classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238 : Implémentez les méthodes de sérialisation](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120 : Constructeurs de sérialisation sécurisé](../code-quality/ca2120-secure-serialization-constructors.md)