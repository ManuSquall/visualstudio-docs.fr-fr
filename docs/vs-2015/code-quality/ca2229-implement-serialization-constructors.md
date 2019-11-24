---
title: 'CA2229 : implémenter des constructeurs de sérialisation | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662843"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229 : Implémentez des constructeurs de sérialisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le type implémente l’interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, n’est pas un délégué ou une interface, et l’une des conditions suivantes est remplie :

- Le type n’a pas de constructeur qui accepte un objet <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> et un objet <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (la signature du constructeur de sérialisation).

- Le type est non scellé et le modificateur d’accès de son constructeur de sérialisation n’est pas protégé (Family).

- Le type est sealed et le modificateur d’accès de son constructeur de sérialisation n’est pas privé.

## <a name="rule-description"></a>Description de la règle
 Cette règle s’applique aux types qui prennent en charge la sérialisation personnalisée. Un type prend en charge la sérialisation personnalisée s’il implémente l’interface <xref:System.Runtime.Serialization.ISerializable>. Le constructeur de sérialisation est requis pour désérialiser ou recréer des objets qui ont été sérialisés à l’aide de la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas une violation de la règle. Le type ne sera pas désérialisé et ne fonctionnera pas dans de nombreux scénarios.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui satisfait la règle.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
