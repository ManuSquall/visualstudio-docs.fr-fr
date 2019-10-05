---
title: 'CA2229 : Implémentez des constructeurs de sérialisation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d148efb87c8516b34342a8c9d16b63364a2eae16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231006"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229 : Implémentez des constructeurs de sérialisation

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Le type implémente l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, n’est pas un délégué ou une interface, et l’une des conditions suivantes est remplie :

- Le type n’a pas de constructeur qui accepte un <xref:System.Runtime.Serialization.SerializationInfo> objet et un <xref:System.Runtime.Serialization.StreamingContext> objet (la signature du constructeur de sérialisation).

- Le type est non scellé et le modificateur d’accès de son constructeur de sérialisation n’est pas protégé (Family).

- Le type est sealed et le modificateur d’accès de son constructeur de sérialisation n’est pas privé.

## <a name="rule-description"></a>Description de la règle

Cette règle s’applique aux types qui prennent en charge la sérialisation personnalisée. Un type prend en charge la sérialisation personnalisée s’il implémente l' <xref:System.Runtime.Serialization.ISerializable> interface. Le constructeur de sérialisation est requis pour désérialiser, ou recréer, les objets qui ont été sérialisés à <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> l’aide de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas une violation de la règle. Le type ne sera pas désérialisé et ne fonctionnera pas dans de nombreux scénarios.

## <a name="example"></a>Exemple

L’exemple suivant montre un type qui satisfait la règle.

[!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Règles associées

[CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
