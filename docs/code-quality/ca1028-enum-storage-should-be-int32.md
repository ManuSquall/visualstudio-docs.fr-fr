---
title: 'CA1028 : Enum Storage doit être Int32'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: eee81a96e6841aa77e2056a95bd18979724b62e5
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842392"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028 : Enum Storage doit être Int32

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Le type sous-jacent d’une énumération n’est pas <xref:System.Int32?displayProperty=fullName>.

Par défaut, cette règle examine uniquement les énumérations publiques, mais il s’agit de [configurable](#configurability).

## <a name="rule-description"></a>Description de la règle

Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le <xref:System.Int32?displayProperty=fullName> type de données est utilisé pour stocker la valeur de constante. Même si vous pouvez modifier ce type sous-jacent, il n’est pas nécessaire ni recommandé pour la plupart des scénarios. Aucun gain de performances de manière significative n’est obtenue à l’aide d’un type de données est inférieur à <xref:System.Int32>. Si vous ne pouvez pas utiliser le type de données par défaut, vous devez utiliser une de le système CLS (Common Language)-des types intégraux conformes, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, ou <xref:System.Int64> pour vous assurer que toutes les valeurs de l’énumération peuvent être représentées dans Langages de programmation conformes CLS.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, sauf si les problèmes de compatibilité ou de taille existent, utilisez <xref:System.Int32>. Pour les situations où <xref:System.Int32> n’est pas assez grand pour contenir les valeurs, utilisez <xref:System.Int64>. Si la compatibilité descendante requiert un type de données plus petits, utilisez <xref:System.Byte> ou <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimer un avertissement de cette règle uniquement si des problèmes de compatibilité descendante le requièrent. Dans les applications, non-respect de cette règle généralement ne provoque pas de problèmes. Dans les bibliothèques, où l’interopérabilité des langages est requise, non-respect de cette règle peut nuire aux utilisateurs.

## <a name="configurability"></a>Possibilités de configuration

Si vous exécutez cette règle à partir de [analyseurs FxCop](install-fxcop-analyzers.md) (et non par le biais d’analyse statique du code), vous pouvez configurer les parties de votre codebase pour exécuter cette règle sur, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement par rapport à la surface d’API non publics, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Vous pouvez configurer cette option pour simplement cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemple de violation

L’exemple suivant montre deux énumérations qui n’utilisent pas le type de données sous-jacent recommandé.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemple de comment la corriger

L’exemple suivant résout la violation précédente en modifiant le type de données sous-jacent <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1008 : Les enums doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700 : Ne nommez pas les valeurs enum 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 : N’ajoutez pas de valeurs d’énumération avec le nom de type préfixe](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>