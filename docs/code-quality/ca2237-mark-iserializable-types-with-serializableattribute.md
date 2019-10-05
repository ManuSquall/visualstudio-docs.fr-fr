---
title: 'CA2237 : Marquer les types ISerializable avec SerializableAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237939"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237 : Marquer les types ISerializable avec SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type visible de l’extérieur implémente <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> l’interface et le type n’est pas marqué <xref:System.SerializableAttribute?displayProperty=fullName> avec l’attribut. La règle ignore les types dérivés dont le type de base n’est pas sérialisable.

## <a name="rule-description"></a>Description de la règle
Pour être reconnus par le Common Language Runtime comme sérialisable, les types doivent être marqués avec l' <xref:System.SerializableAttribute> attribut même si le type utilise une routine de sérialisation personnalisée par le biais de <xref:System.Runtime.Serialization.ISerializable> l’implémentation de l’interface.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, appliquez l' <xref:System.SerializableAttribute> attribut au type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un avertissement de cette règle pour les classes d’exception, car elles doivent être sérialisables pour fonctionner correctement entre les domaines d’application.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole la règle. Supprimez les <xref:System.SerializableAttribute> marques de commentaire de la ligne d’attribut pour satisfaire la règle.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2236 Appeler les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240 Implémenter ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238 Implémenter les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239 Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120 Sécuriser les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)