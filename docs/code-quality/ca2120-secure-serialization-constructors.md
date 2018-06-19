---
title: 'CA2120 : Sécurisez les constructeurs de sérialisation'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 449258d04b6a47fef42c56637a4de48a4e5d1d12
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915389"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120 : Sécurisez les constructeurs de sérialisation
|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le type implémente le <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, n’est pas un délégué ou une interface et est déclaré dans un assembly qui autorise les appelants partiellement approuvés. Le type a un constructeur qui accepte un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objet et un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objet (la signature du constructeur de sérialisation). Ce constructeur n’est pas sécurisé par une vérification de sécurité, mais au moins des constructeurs normaux dans le type est sécurisé.

## <a name="rule-description"></a>Description de la règle
 Cette règle s’applique pour les types qui prennent en charge la sérialisation personnalisée. Un type prend en charge la sérialisation personnalisée s’il implémente la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface. Le constructeur de sérialisation est requis et est utilisé pour désérialiser ou recréer des objets qui ont été sérialisés à l’aide de la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (méthode). Étant donné que le constructeur de sérialisation alloue et initialise les objets, les vérifications de sécurité qui sont présentes sur les constructeurs normaux doivent également être présentes sur le constructeur de sérialisation. Si vous ne respectez pas cette règle, les appelants qui n’a pas sinon créer une instance peuvent utiliser le constructeur de sérialisation pour ce faire.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, protégez le constructeur de sérialisation avec des demandes de sécurité qui sont identiques à celles qui protègent d’autres constructeurs.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas une violation de la règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui enfreint la règle.

 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>