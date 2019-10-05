---
title: 'CA1008 : Les enums doivent avoir la valeur zéro'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236487"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008 : Les enums doivent avoir la valeur zéro

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture : lorsque vous êtes invité à ajouter une valeur **None** à une énumération sans indicateur. Avec rupture : lorsque vous êtes invité à renommer ou à supprimer des valeurs d’énumération.|

## <a name="cause"></a>Cause

Une énumération sans application <xref:System.FlagsAttribute?displayProperty=fullName> ne définit pas un membre dont la valeur est égale à zéro. Ou bien, une énumération qui a <xref:System.FlagsAttribute> un appliqué définit un membre qui a une valeur de zéro, mais son nom n’est pas’none'. Ou, l’énumération définit plusieurs membres dont la valeur est égale à zéro.

Par défaut, cette règle examine uniquement les énumérations visibles de l’extérieur, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

La valeur par défaut d’une énumération non initialisée, comme d’autres types valeur, est zéro. Une énumération non affectée par des indicateurs doit définir un membre qui a la valeur zéro afin que la valeur par défaut soit une valeur valide de l’énumération. Le cas échéant, nommez le membre « None ». Sinon, affectez la valeur zéro au membre le plus fréquemment utilisé. Par défaut, si la valeur du premier membre de l’énumération n’est pas définie dans la déclaration, sa valeur est zéro.

Si une énumération qui a <xref:System.FlagsAttribute> le appliqué définit un membre de valeur zéro, son nom doit être’none’pour indiquer qu’aucune valeur n’a été définie dans l’énumération. L’utilisation d’un membre de valeur zéro à d’autres fins est contraire à l’utilisation <xref:System.FlagsAttribute> de dans la mesure où les opérateurs de bits and et or sont inutiles avec le membre. Cela implique que la valeur zéro doit être affectée à un seul membre. Si plusieurs membres ayant la valeur zéro se produisent dans une énumération avec attributs d' `Enum.ToString()` indicateurs, retourne des résultats incorrects pour les membres qui ne sont pas nuls.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle pour les énumérations non attribuées par des indicateurs, définissez un membre qui a la valeur zéro ; Il s’agit d’une modification sans rupture. Pour les énumérations attribuées par des indicateurs qui définissent un membre de valeur zéro, nommez ce membre’none’et supprimez tous les autres membres qui ont une valeur de zéro ; Il s’agit d’une modification avec rupture.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle, à l’exception des énumérations attribuées par des indicateurs qui ont déjà été expédiées.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemple

L’exemple suivant montre deux énumérations qui satisfont à la règle et une `BadTraceOptions`énumération,, qui violent la règle.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Règles associées

- [CA2217 Ne Marquez pas les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700 Ne nommez pas les valeurs enum’reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 Ne pas préfixer les valeurs d’énumération avec le nom de type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028 Le stockage enum doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027 Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Enum?displayProperty=fullName>