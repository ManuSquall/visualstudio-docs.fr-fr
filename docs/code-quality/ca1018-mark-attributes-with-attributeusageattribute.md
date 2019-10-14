---
title: 'CA1018 : Marquer les attributs avec AttributeUsageAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306137"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018 : Marquer les attributs avec AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
L’attribut <xref:System.AttributeUsageAttribute?displayProperty=fullName> n’est pas présent sur l’attribut personnalisé.

## <a name="rule-description"></a>Description de la règle
Lorsque vous définissez un attribut personnalisé, marquez-le à l’aide de <xref:System.AttributeUsageAttribute> pour indiquer à quel endroit du code source l’attribut personnalisé peut être appliqué. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. Par exemple, vous pouvez définir un attribut qui identifie la personne responsable de la maintenance et de l’amélioration de chaque type dans une bibliothèque, et cette responsabilité est toujours assignée au niveau du type. Dans ce cas, les compilateurs doivent activer l’attribut sur les classes, les énumérations et les interfaces, mais ne doivent pas l’activer sur des méthodes, des événements ou des propriétés. Les stratégies et les procédures de l’organisation déterminent si l’attribut doit être activé sur les assemblys.

L’énumération <xref:System.AttributeTargets?displayProperty=fullName> définit les cibles que vous pouvez spécifier pour un attribut personnalisé. Si vous omettez <xref:System.AttributeUsageAttribute>, votre attribut personnalisé est valide pour toutes les cibles, comme défini par la valeur `All` de l’énumération <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, spécifiez des cibles pour l’attribut à l’aide de <xref:System.AttributeUsageAttribute>. Lisez l'exemple suivant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Vous devez corriger une violation de cette règle au lieu d’exclure le message. Même si l’attribut hérite <xref:System.AttributeUsageAttribute>, l’attribut doit être présent pour simplifier la maintenance du code.

## <a name="example"></a>Exemple
L’exemple suivant définit deux attributs. `BadCodeMaintainerAttribute` omet l’instruction <xref:System.AttributeUsageAttribute> de manière incorrecte et `GoodCodeMaintainerAttribute` implémente correctement l’attribut décrit précédemment dans cette section. Notez que la propriété `DeveloperName` est requise par la règle de conception [CA1019 : Définir des accesseurs pour les arguments d’attribut @ no__t-0 et est inclus par exhaustivité.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Règles associées
@NO__T 0CA1019 : Définir des accesseurs pour les arguments d’attribut @ no__t-0

@NO__T 0CA1813 : Évitez les attributs non scellés @ no__t-0

## <a name="see-also"></a>Voir aussi

- [Attributs](/dotnet/standard/design-guidelines/attributes)