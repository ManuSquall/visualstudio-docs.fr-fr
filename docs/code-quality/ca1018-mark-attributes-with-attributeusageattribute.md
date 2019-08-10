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
ms.openlocfilehash: 78917bcd4c67e1da205595bac07c8e0e5947318d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923061"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018 : Marquer les attributs avec AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Catégorie|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
L' <xref:System.AttributeUsageAttribute?displayProperty=fullName> attribut n’est pas présent sur l’attribut personnalisé.

## <a name="rule-description"></a>Description de la règle
Lorsque vous définissez un attribut personnalisé, marquez-le <xref:System.AttributeUsageAttribute> à l’aide de pour indiquer où l’attribut personnalisé peut être appliqué dans le code source. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. Par exemple, vous pouvez définir un attribut qui identifie la personne responsable de la maintenance et de l’amélioration de chaque type dans une bibliothèque, et cette responsabilité est toujours assignée au niveau du type. Dans ce cas, les compilateurs doivent activer l’attribut sur les classes, les énumérations et les interfaces, mais ne doivent pas l’activer sur des méthodes, des événements ou des propriétés. Les stratégies et les procédures de l’organisation déterminent si l’attribut doit être activé sur les assemblys.

L' <xref:System.AttributeTargets?displayProperty=fullName> énumération définit les cibles que vous pouvez spécifier pour un attribut personnalisé. Si vous omettez <xref:System.AttributeUsageAttribute>, votre attribut personnalisé est valide pour toutes les cibles, comme défini par la `All` valeur de <xref:System.AttributeTargets> l’énumération.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, spécifiez des cibles pour l’attribut <xref:System.AttributeUsageAttribute>à l’aide de. Consultez l’exemple qui suit.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Vous devez corriger une violation de cette règle au lieu d’exclure le message. Même si l’attribut hérite <xref:System.AttributeUsageAttribute>de, l’attribut doit être présent pour simplifier la maintenance du code.

## <a name="example"></a>Exemple
L’exemple suivant définit deux attributs. `BadCodeMaintainerAttribute`omet de manière incorrecte <xref:System.AttributeUsageAttribute> l’instruction, `GoodCodeMaintainerAttribute` et implémente correctement l’attribut décrit plus haut dans cette section. Notez que la propriété `DeveloperName` est requise par la règle [de conception ca1019: Définissez des accesseurs pour les](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) arguments d’attribut et est inclus par exhaustivité.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1019 Définir des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813 Éviter les attributs non scellés](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Voir aussi

- [Attributs](/dotnet/standard/design-guidelines/attributes)