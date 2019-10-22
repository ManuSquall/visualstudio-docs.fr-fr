---
title: 'CA2240 : Implémentez ISerializable correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0abc95811dc870abbfaa583fbaa7705302a70781
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670170"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240 : Implémentez ISerializable comme il se doit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur peut être assigné à l’interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> et l’une des conditions suivantes est vraie :

- Le type hérite de, mais ne remplace pas la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> et le type déclare des champs d’instance qui ne sont pas marqués avec l’attribut <xref:System.NonSerializedAttribute?displayProperty=fullName>.

- Le type n’est pas sealed et le type implémente une méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> qui n’est pas visible de l’extérieur et est substituable.

## <a name="rule-description"></a>Description de la règle
 Les champs d’instance déclarés dans un type qui hérite de l’interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> ne sont pas inclus automatiquement dans le processus de sérialisation. Pour inclure les champs, le type doit implémenter la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> et le constructeur de sérialisation. Si les champs ne doivent pas être sérialisés, appliquez l’attribut <xref:System.NonSerializedAttribute> aux champs pour indiquer explicitement la décision.

 Dans les types non scellés, les implémentations de la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> doivent être visibles de l’extérieur. Par conséquent, la méthode peut être appelée par des types dérivés et est substituable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, rendez la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> visible et substituable et assurez-vous que tous les champs d’instance sont inclus dans le processus de sérialisation ou explicitement marqués avec l’attribut <xref:System.NonSerializedAttribute>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux types sérialisables qui violent la règle.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout les deux violations précédentes en fournissant une implémentation remplaçable de [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) sur la classe Book et en fournissant une implémentation de <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> sur la classe de la bibliothèque.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238 : Implémentez les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)
