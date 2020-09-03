---
title: 'CA1008 : les enums doivent avoir une valeur zéro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548341"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008 : Les enums doivent avoir la valeur zéro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture : lorsque vous êtes invité à ajouter une valeur **None** à une énumération sans indicateur. Avec rupture : lorsque vous êtes invité à renommer ou à supprimer des valeurs d’énumération.|

## <a name="cause"></a>Cause :
 Une énumération sans application <xref:System.FlagsAttribute?displayProperty=fullName> ne définit pas un membre qui a une valeur égale à zéro ; ou une énumération à laquelle est appliqué <xref:System.FlagsAttribute> définit un membre dont la valeur est égale à zéro, mais dont le nom n’est pas’none', ou l’énumération définit plusieurs membres dont la valeur est zéro.

## <a name="rule-description"></a>Description de la règle
 La valeur par défaut d’une énumération non initialisée, comme d’autres types valeur, est zéro. Une énumération avec attributs sans indicateur doit définir un membre qui a la valeur zéro afin que la valeur par défaut soit une valeur valide de l’énumération. Le cas échéant, nommez le membre « None ». Sinon, affectez la valeur zéro au membre le plus fréquemment utilisé. Notez que, par défaut, si la valeur du premier membre de l’énumération n’est pas définie dans la déclaration, sa valeur est zéro.

 Si une énumération qui a le <xref:System.FlagsAttribute> appliqué définit un membre de valeur zéro, son nom doit être’none’pour indiquer qu’aucune valeur n’a été définie dans l’énumération. L’utilisation d’un membre de valeur zéro à d’autres fins est contraire à l’utilisation de dans la mesure <xref:System.FlagsAttribute> où les opérateurs de bits and et or sont inutiles avec le membre. Cela implique que la valeur zéro doit être affectée à un seul membre. Notez que si plusieurs membres ayant la valeur zéro se produisent dans une énumération avec attributs d’indicateurs, `Enum.ToString()` retourne des résultats incorrects pour les membres qui ne sont pas nuls.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle pour les énumérations avec attributs non-Flags, définissez un membre qui a la valeur zéro ; Il s’agit d’une modification sans rupture. Pour les énumérations attribuées par des indicateurs qui définissent un membre de valeur zéro, nommez ce membre’none’et supprimez tous les autres membres qui ont une valeur de zéro ; Il s’agit d’une modification avec rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, à l’exception des énumérations attribuées par des indicateurs qui ont déjà été expédiées.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux énumérations qui satisfont à la règle et une énumération, `BadTraceOptions` , qui violent la règle.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700 : Ne nommez pas les valeurs enum 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028 : Enum Storage doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Enum?displayProperty=fullName>
