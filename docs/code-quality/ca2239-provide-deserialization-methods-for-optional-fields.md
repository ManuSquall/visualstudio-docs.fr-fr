---
title: 'CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cf2e30956879c0c61bb57d65b89445962f34959a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237892"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type a un champ qui est marqué avec l' <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> attribut et le type ne fournit pas de méthodes de gestion des événements de désérialisation.

## <a name="rule-description"></a>Description de la règle
L' <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribut n’a aucun effet sur la sérialisation ; un champ marqué avec l’attribut est sérialisé. Toutefois, le champ est ignoré lors de la désérialisation et conserve la valeur par défaut associée à son type. Les gestionnaires d’événements de désérialisation doivent être déclarés pour définir le champ pendant le processus de désérialisation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, ajoutez les méthodes de gestion des événements de désérialisation au type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le champ doit être ignoré pendant le processus de désérialisation.

## <a name="example"></a>Exemple
L’exemple suivant illustre un type avec des méthodes facultatives de gestion des événements de désérialisation et de champ.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA2236 Appeler les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240 Implémenter ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238 Implémenter les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120 Sécuriser les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)