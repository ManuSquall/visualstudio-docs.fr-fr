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
ms.openlocfilehash: 47a934a6e35296927eea64465ff8e7007219bec5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236096"
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

Par défaut, cette règle examine uniquement les énumérations publiques, mais elle peut [être configurée](#configurability).

## <a name="rule-description"></a>Description de la règle

Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le <xref:System.Int32?displayProperty=fullName> type de données est utilisé pour stocker la valeur constante. Même si vous pouvez modifier ce type sous-jacent, il n’est pas nécessaire ou recommandé pour la plupart des scénarios. Aucun gain de performances significatif n’est obtenu à l’aide d’un type <xref:System.Int32>de données inférieur à. Si vous ne pouvez pas utiliser le type de données par défaut, vous devez utiliser l’un des types intégraux conformes CLS (Common Language <xref:System.Byte>System <xref:System.Int16>) <xref:System.Int32>,, <xref:System.Int64> , ou pour vous assurer que toutes les valeurs de l’énumération peuvent être représentées dans Langages de programmation conformes à CLS.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, à moins que des problèmes de taille ou <xref:System.Int32>de compatibilité n’existent, utilisez. Dans les situations <xref:System.Int32> où n’est pas assez grand pour contenir les valeurs <xref:System.Int64>, utilisez. Si la compatibilité descendante requiert un type de données <xref:System.Byte> plus <xref:System.Int16>petit, utilisez ou.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Supprimez un avertissement de cette règle uniquement si des problèmes de compatibilité descendante l’exigent. Dans les applications, l’impossibilité de se conformer à cette règle n’entraîne généralement pas de problèmes. Dans les bibliothèques, où l’interopérabilité des langages est requise, le non-respect de cette règle peut nuire à vos utilisateurs.

## <a name="configurability"></a>Configurabilité

Si vous exécutez cette règle à partir d' [analyseurs FxCop](install-fxcop-analyzers.md) (et non avec l’analyse héritée), vous pouvez configurer les parties de votre code base sur lesquelles exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet :

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Vous pouvez configurer cette option uniquement pour cette règle, pour toutes les règles ou pour toutes les règles de cette catégorie (conception). Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemple de violation

L’exemple suivant montre deux énumérations qui n’utilisent pas le type de données sous-jacent recommandé.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemple de résolution

L’exemple suivant résout la violation précédente en remplaçant le type de <xref:System.Int32>données sous-jacent par.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Règles associées

- [CA1008 Les enums doivent avoir une valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027 Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217 Ne Marquez pas les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700 Ne nommez pas les valeurs enum’reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 Ne pas préfixer les valeurs d’énumération avec le nom de type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>