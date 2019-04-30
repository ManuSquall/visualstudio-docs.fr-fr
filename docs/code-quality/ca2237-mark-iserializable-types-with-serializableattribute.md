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
ms.openlocfilehash: 7ccc7819de8e79cae86a60fd015e6b8268c2456c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541647"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237 : Marquer les types ISerializable avec SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type visible extérieurement implémente le <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface et le type n’est pas marqué avec le <xref:System.SerializableAttribute?displayProperty=fullName> attribut. La règle ignore les types dérivés dont le type de base n’est pas sérialisable.

## <a name="rule-description"></a>Description de la règle
 Pour être reconnus par le common language runtime comme sérialisables, les types doivent être marqués avec le <xref:System.SerializableAttribute> attribut même si le type utilise une routine de sérialisation personnalisée via l’implémentation de la <xref:System.Runtime.Serialization.ISerializable> interface.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appliquez le <xref:System.SerializableAttribute> pour le type d’attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas d’avertissement de cette règle pour les classes d’exception, car ils doivent être sérialisables pour fonctionner correctement sur les domaines d’application.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle. Supprimez les commentaires de la <xref:System.SerializableAttribute> ligne pour satisfaire la règle de l’attribut.

 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2236 : Appeler des méthodes de classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238 : Implémentez les méthodes de sérialisation](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120 : Constructeurs de sérialisation sécurisé](../code-quality/ca2120-secure-serialization-constructors.md)