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
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666710"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type dérive d’un type qui implémente l’interface <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, et l’une des conditions suivantes est vraie :

- Le type implémente le constructeur de sérialisation, autrement dit, un constructeur avec la signature de paramètre <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, mais il n’appelle pas le constructeur de sérialisation du type de base.

- Le type implémente la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> mais n’appelle pas la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> du type de base.

## <a name="rule-description"></a>Description de la règle
 Dans un processus de sérialisation personnalisé, un type implémente la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> pour sérialiser ses champs et le constructeur de sérialisation pour désérialiser les champs. Si le type dérive d’un type qui implémente l’interface <xref:System.Runtime.Serialization.ISerializable>, le type de base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode et le constructeur de sérialisation doivent être appelés pour sérialiser/désérialiser les champs du type de base. Dans le cas contraire, le type ne sera pas sérialisé et désérialisé correctement. Notez que si le type dérivé n’ajoute pas de nouveaux champs, le type n’a pas besoin d’implémenter la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> ni le constructeur de sérialisation ni d’appeler les équivalents de type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez le type de base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> méthode ou du constructeur de sérialisation à partir de la méthode ou du constructeur de type dérivé correspondant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type dérivé qui satisfait la règle en appelant le constructeur de sérialisation et la méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> de la classe de base.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238 : Implémentez les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)
