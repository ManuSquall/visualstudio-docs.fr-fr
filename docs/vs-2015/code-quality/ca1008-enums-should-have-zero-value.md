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
ms.openlocfilehash: fbc7775d4ec41822b866868a6db6bceb353af989
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668931"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008 : Les enums doivent avoir la valeur zéro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture : lorsque vous êtes invité à ajouter une valeur **None** à une énumération sans indicateur. Avec rupture : lorsque vous êtes invité à renommer ou à supprimer des valeurs d’énumération.|

## <a name="cause"></a>Cause
 Une énumération sans <xref:System.FlagsAttribute?displayProperty=fullName> appliquée ne définit pas un membre dont la valeur est égale à zéro ; ou une énumération qui a un <xref:System.FlagsAttribute> appliqué définit un membre qui a une valeur de zéro, mais son nom n’est pas’none', ou l’énumération définit plusieurs membres de valeur zéro.

## <a name="rule-description"></a>Description de la règle
 La valeur par défaut d’une énumération non initialisée, comme d’autres types valeur, est zéro. Une énumération avec attributs sans indicateur doit définir un membre qui a la valeur zéro afin que la valeur par défaut soit une valeur valide de l’énumération. Le cas échéant, nommez le membre « None ». Sinon, affectez la valeur zéro au membre le plus fréquemment utilisé. Notez que, par défaut, si la valeur du premier membre de l’énumération n’est pas définie dans la déclaration, sa valeur est zéro.

 Si une énumération avec l' <xref:System.FlagsAttribute> appliquée définit un membre de valeur zéro, son nom doit être’none’pour indiquer qu’aucune valeur n’a été définie dans l’énumération. L’utilisation d’un membre de valeur zéro à d’autres fins est contraire à l’utilisation du <xref:System.FlagsAttribute> dans le sens où les opérateurs de bits and et OR sont inutiles avec le membre. Cela implique que la valeur zéro doit être affectée à un seul membre. Notez que si plusieurs membres ayant la valeur zéro se produisent dans une énumération avec attributs d’indicateurs, `Enum.ToString()` retourne des résultats incorrects pour les membres qui ne sont pas nuls.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle pour les énumérations avec attributs non-Flags, définissez un membre qui a la valeur zéro ; Il s’agit d’une modification sans rupture. Pour les énumérations attribuées par des indicateurs qui définissent un membre de valeur zéro, nommez ce membre’none’et supprimez tous les autres membres qui ont une valeur de zéro ; Il s’agit d’une modification avec rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, à l’exception des énumérations attribuées par des indicateurs qui ont déjà été expédiées.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux énumérations qui satisfont la règle et une énumération, `BadTraceOptions`, qui transgressent la règle.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700 : Ne nommez pas les valeurs d’énumération 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712 : Ne préfixez pas les valeurs d’énumération avec le nom du type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028 : Le stockage de l’énumération doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Enum?displayProperty=fullName>
