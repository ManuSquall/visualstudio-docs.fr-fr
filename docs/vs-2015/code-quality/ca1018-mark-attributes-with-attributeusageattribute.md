---
title: 'CA1018 : Marquer les attributs avec AttributeUsageAttribute | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 628eae181fa685e5173030ebac94387edfe4a194
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947846"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018 : Marquer les attributs avec AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le <xref:System.AttributeUsageAttribute?displayProperty=fullName> attribut n’est pas présent sur l’attribut personnalisé.

## <a name="rule-description"></a>Description de la règle
 Lorsque vous définissez un attribut personnalisé, marquez-le à l’aide de <xref:System.AttributeUsageAttribute> pour indiquer où l’attribut personnalisé peut être appliqué dans le code source. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. Par exemple, vous pouvez définir un attribut qui identifie la personne qui est responsable de la gestion et l’amélioration de chaque type dans une bibliothèque, et que la responsabilité est toujours affectée au niveau du type. Dans ce cas, les compilateurs doivent activer l’attribut sur les classes, énumérations et interfaces, mais ne devraient pas l’activer sur les méthodes, événements ou propriétés. Les stratégies d’organisation et les procédures seraient déterminent si l’attribut doit être activé sur les assemblys.

 Le <xref:System.AttributeTargets?displayProperty=fullName> énumération définit les cibles que vous pouvez spécifier pour un attribut personnalisé. Si vous omettez <xref:System.AttributeUsageAttribute>, votre attribut personnalisé sera valide pour toutes les cibles, tel que défini par le `All` valeur <xref:System.AttributeTargets> énumération.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, spécifiez des cibles pour l’attribut à l’aide de <xref:System.AttributeUsageAttribute>. Lisez l'exemple suivant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous devez corriger une violation de cette règle au lieu d’exclure le message. Même si l’attribut hérite <xref:System.AttributeUsageAttribute>, l’attribut doit être présent pour simplifier la maintenance du code.

## <a name="example"></a>Exemple
 L’exemple suivant définit deux attributs. `BadCodeMaintainerAttribute` omet le <xref:System.AttributeUsageAttribute> instruction, et `GoodCodeMaintainerAttribute` implémente correctement l’attribut qui est décrite plus haut dans cette section. Notez que la propriété `DeveloperName` est requis par la règle de conception [CA1019 : Définir des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) et est incluse par souci d’exhaustivité.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1019 : Définir des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Voir aussi
 [Attributs](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
