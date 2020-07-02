---
title: 'Ca2236 : appelez les méthodes de la classe de base sur les types ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a03192ac8a5b59558dc39a32f55e8177dc249365
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545182"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type dérive d’un type qui implémente l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, et l’une des conditions suivantes est vraie :

- Le type implémente le constructeur de sérialisation, autrement dit, un constructeur avec la <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> signature de paramètre, mais n’appelle pas le constructeur de sérialisation du type de base.

- Le type implémente la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> méthode, mais n’appelle pas la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode du type de base.

## <a name="rule-description"></a>Description de la règle
 Dans un processus de sérialisation personnalisé, un type implémente la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode pour sérialiser ses champs et le constructeur de sérialisation pour désérialiser les champs. Si le type dérive d’un type qui implémente l' <xref:System.Runtime.Serialization.ISerializable> interface, la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode de type de base et le constructeur de sérialisation doivent être appelés pour sérialiser/désérialiser les champs du type de base. Dans le cas contraire, le type ne sera pas sérialisé et désérialisé correctement. Notez que si le type dérivé n’ajoute pas de nouveaux champs, le type n’a pas besoin d’implémenter la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode ni le constructeur de sérialisation ni d’appeler les équivalents de type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez la méthode de type <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> de base ou le constructeur de sérialisation à partir de la méthode ou du constructeur de type dérivé correspondant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type dérivé qui satisfait la règle en appelant le constructeur de sérialisation et <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> la méthode de la classe de base.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2240 : Implémentez ISerializable comme il se doit](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238 : Implémentez les méthodes de sérialisation comme il se doit](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)
