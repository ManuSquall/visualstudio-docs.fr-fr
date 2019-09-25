---
title: "CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0b5966c9685bc4bbc5ba997f8acf47abbbfca1a2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234108"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une énumération contient un membre dont le nom commence par le nom de type de l’énumération.

## <a name="rule-description"></a>Description de la règle
Les noms des membres de l’énumération n’ont pas le préfixe du nom de type, car les informations de type doivent être fournies par les outils de développement.

Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire à pour apprendre une nouvelle bibliothèque de logiciels et augmente la confiance des clients à ce que la bibliothèque ait été développée par une personne expérimentée dans le développement de code géré.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez le préfixe de nom de type du membre de l’énumération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre une énumération incorrectement nommée suivie de la version corrigée.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1711 Les identificateurs ne doivent pas avoir de suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027 Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217 Ne Marquez pas les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Enum?displayProperty=fullName>