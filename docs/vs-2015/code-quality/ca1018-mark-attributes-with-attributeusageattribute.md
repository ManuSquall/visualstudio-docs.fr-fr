---
title: 'CA1018 : marquer les attributs avec AttributeUsageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535055"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018 : Marquer les attributs avec AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 L' <xref:System.AttributeUsageAttribute?displayProperty=fullName> attribut n’est pas présent sur l’attribut personnalisé.

## <a name="rule-description"></a>Description de la règle
 Lorsque vous définissez un attribut personnalisé, marquez-le à l’aide <xref:System.AttributeUsageAttribute> de pour indiquer où l’attribut personnalisé peut être appliqué dans le code source. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. Par exemple, vous pouvez définir un attribut qui identifie la personne responsable de la maintenance et de l’amélioration de chaque type dans une bibliothèque, et cette responsabilité est toujours assignée au niveau du type. Dans ce cas, les compilateurs doivent activer l’attribut sur les classes, les énumérations et les interfaces, mais ne doivent pas l’activer sur des méthodes, des événements ou des propriétés. Les stratégies et les procédures de l’organisation déterminent si l’attribut doit être activé sur les assemblys.

 L' <xref:System.AttributeTargets?displayProperty=fullName> énumération définit les cibles que vous pouvez spécifier pour un attribut personnalisé. Si vous omettez <xref:System.AttributeUsageAttribute> , votre attribut personnalisé est valide pour toutes les cibles, comme défini par la `All` valeur de l' <xref:System.AttributeTargets> énumération.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, spécifiez des cibles pour l’attribut à l’aide de <xref:System.AttributeUsageAttribute> . Consultez l’exemple qui suit.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous devez corriger une violation de cette règle au lieu d’exclure le message. Même si l’attribut hérite <xref:System.AttributeUsageAttribute> de, l’attribut doit être présent pour simplifier la maintenance du code.

## <a name="example"></a>Exemple
 L’exemple suivant définit deux attributs. `BadCodeMaintainerAttribute`omet de manière incorrecte l' <xref:System.AttributeUsageAttribute> instruction, et `GoodCodeMaintainerAttribute` implémente correctement l’attribut décrit plus haut dans cette section. Notez que la propriété `DeveloperName` est requise par la règle de conception [ca1019 : définir des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) et est incluse par exhaustivité.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1019 : Définir des accesseurs pour les arguments d'attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Voir aussi
 [Attributs](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
