---
title: 'CA2238 : Implémentez les méthodes de sérialisation | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d9c23ef8da970a29057c0e299d5b8d12dda524
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001825"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238 : Implémentez les méthodes de sérialisation comme il se doit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA2238 : Implémentez les méthodes de sérialisation](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly) sur docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Avec rupture - Si la méthode est visible en dehors de l’assembly.<br /><br /> Sans rupture - Si la méthode n’est pas visible en dehors de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée.  
  
## <a name="rule-description"></a>Description de la règle  
 Une méthode est désignée d’un gestionnaire d’événements de sérialisation en appliquant l’un des attributs d’événement de sérialisation suivants :  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
  Gestionnaires d’événements de sérialisation acceptent un seul paramètre de type <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, retour `void`et avez `private` visibilité.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, corrigez la signature, le type de retour ou la visibilité du Gestionnaire d’événements de sérialisation.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre des gestionnaires d’événements sérialisation correctement déclarée.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2236 : Appeler des méthodes de classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120 : Constructeurs de sérialisation sécurisé](../code-quality/ca2120-secure-serialization-constructors.md)
