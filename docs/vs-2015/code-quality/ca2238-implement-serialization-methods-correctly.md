---
title: 'CA2238 : implémenter les méthodes de sérialisation correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 98e825fd5543b928569b99218c9054aff666e0fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545143"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238 : Implémentez les méthodes de sérialisation comme il se doit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [CA2238 : implémenter les méthodes de sérialisation correctement](/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).

|Élément|Valeur|
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Category|Microsoft. usage|
|Modification avec rupture|Avec rupture : si la méthode est visible à l’extérieur de l’assembly.<br /><br /> Sans rupture : si la méthode n’est pas visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause :
 Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée.

## <a name="rule-description"></a>Description de la règle
 Une méthode est désignée comme un gestionnaire d’événements de sérialisation en appliquant l’un des attributs d’événement de sérialisation suivants :

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Les gestionnaires d’événements de sérialisation acceptent un seul paramètre de type <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> , retourne `void` et ont une `private` visibilité.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez la signature, le type de retour ou la visibilité du gestionnaire d’événements de sérialisation.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre des gestionnaires d’événements de sérialisation correctement déclarés.

 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240 : Implémentez ISerializable comme il se doit](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md)
