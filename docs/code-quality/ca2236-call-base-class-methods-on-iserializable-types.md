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
ms.openlocfilehash: 000ce33b71c13f87f218a15c364fda21b99ccfe4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939721"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type dérive d’un type qui implémente le <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface et une des conditions suivantes est vraie :

- Le type implémente le constructeur de sérialisation, autrement dit, un constructeur avec le <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> signature de paramètre, mais n’appelle ne pas le constructeur de sérialisation du type de base.

- Le type implémente le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> méthode mais n’appelle pas la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode du type de base.

## <a name="rule-description"></a>Description de la règle
 Dans un processus de sérialisation personnalisé, un type implémente le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode pour sérialiser ses champs et le constructeur de sérialisation pour désérialiser les champs. Si le type dérive d’un type qui implémente le <xref:System.Runtime.Serialization.ISerializable> interface, le type de base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> constructeur de sérialisation et de la méthode doit être appelé pour sérialiser/désérialiser les champs du type de base. Sinon, le type ne sera pas sérialisé et désérialisé correctement. Notez que si le type dérivé n’ajoute pas tous les nouveaux champs, le type n’a pas besoin d’implémenter le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode, ni le constructeur de sérialisation ou d’appeler les équivalents de type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez le type de base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> constructeur de sérialisation ou de la méthode à partir de le correspondantes dérivée de méthode de type ou le constructeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type dérivé qui satisfait la règle en appelant le constructeur de sérialisation et <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode de la classe de base.

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238 : Implémentez les méthodes de sérialisation](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120 : Constructeurs de sérialisation sécurisé](../code-quality/ca2120-secure-serialization-constructors.md)