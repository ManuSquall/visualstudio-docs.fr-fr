---
title: 'CA1028 : Enum Storage doit être Int32'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0f9dec006f3684259541811e905eaf75a790c3a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900286"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028 : Enum Storage doit être Int32
|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le type sous-jacent d’une énumération publique n’est pas <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le <xref:System.Int32?displayProperty=fullName> type de données est utilisé pour stocker la valeur de constante. Bien que vous pouvez modifier ce type sous-jacent, il n’est pas nécessaire ou recommandée pour la plupart des scénarios. Notez que l’option aucun gain de performances n’est effectuée à l’aide d’un type de données est inférieur à <xref:System.Int32>. Si vous ne pouvez pas utiliser le type de données par défaut, vous devez utiliser un de le système CLS (Common Language)-des types intégraux conformes, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, ou <xref:System.Int64> pour vous assurer que toutes les valeurs de l’énumération peuvent être représentées dans Langages de programmation conformes CLS.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, sauf si des problèmes de compatibilité ou de taille existent, utilisez <xref:System.Int32>. Pour les situations où <xref:System.Int32> n’est pas suffisamment grande pour contenir les valeurs, utilisez <xref:System.Int64>. Si la compatibilité descendante requiert un type de données plus petit, utilisez <xref:System.Byte> ou <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle uniquement si des problèmes de compatibilité descendante le requièrent. Dans les applications, pas se conformer à cette règle généralement ne provoque pas de problèmes. Dans les bibliothèques, où l’interopérabilité des langages est requise, non-respect de cette règle peut nuire aux utilisateurs.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre deux énumérations qui n’utilisent pas le type de données sous-jacent recommandé.

### <a name="code"></a>Code
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemple de correctif

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en modifiant le type de données sous-jacent <xref:System.Int32>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Règles associées
 [CA1008 : Les énumérations doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700 : Ne nommez pas les valeurs d’énumération 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712 : Ne préfixez pas les valeurs d’énumération avec le nom du type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> <xref:System.Int64?displayProperty=fullName>