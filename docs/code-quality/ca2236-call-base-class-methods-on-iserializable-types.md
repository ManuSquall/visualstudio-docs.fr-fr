---
title: 'CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f0075a6296e839030448c0209c77f1717a5fcb1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920121"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type dérive d’un type qui implémente l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, et l’une des conditions suivantes est vraie:

- Le type implémente le constructeur de sérialisation, autrement dit, un constructeur avec la <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>signature <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> de paramètre, mais n’appelle pas le constructeur de sérialisation du type de base.

- Le type implémente la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> méthode, mais n’appelle pas <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> la méthode du type de base.

## <a name="rule-description"></a>Description de la règle
Dans un processus de sérialisation personnalisé, un type implémente la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode pour sérialiser ses champs et le constructeur de sérialisation pour désérialiser les champs. Si le type dérive d’un type qui implémente l' <xref:System.Runtime.Serialization.ISerializable> interface, la méthode de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> type de base et le constructeur de sérialisation doivent être appelés pour sérialiser/désérialiser les champs du type de base. Dans le cas contraire, le type ne sera pas sérialisé et désérialisé correctement. Notez que si le type dérivé n’ajoute pas de nouveaux champs, le type n’a pas besoin d’implémenter la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode ni le constructeur de sérialisation ni d’appeler les équivalents de type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, appelez la méthode de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> type de base ou le constructeur de sérialisation à partir de la méthode ou du constructeur de type dérivé correspondant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemples
L’exemple suivant montre un type dérivé qui satisfait la règle en appelant le constructeur de sérialisation et <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> la méthode de la classe de base.

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2240 Implémenter ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238 Implémenter les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239 Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120 Sécuriser les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)