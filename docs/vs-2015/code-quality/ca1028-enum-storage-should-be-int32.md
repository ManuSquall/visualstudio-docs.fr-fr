---
title: 'CA1028 : Enum storage doit être Int32 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b7e726299b668a6ea9352bd478ffbd86b51bcc3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590107"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028 : Enum Storage doit être Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1028 : Enum storage doit être Int32](https://docs.microsoft.com/visualstudio/code-quality/ca1028-enum-storage-should-be-int32).

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le type sous-jacent d’une énumération publique n’est pas <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le <xref:System.Int32?displayProperty=fullName> type de données est utilisé pour stocker la valeur de constante. Même si vous pouvez modifier ce type sous-jacent, il n’est pas nécessaire ni recommandé pour la plupart des scénarios. Notez qu’aucun gain de performances de manière significative n’est effectué à l’aide d’un type de données est inférieur à <xref:System.Int32>. Si vous ne pouvez pas utiliser le type de données par défaut, vous devez utiliser une de le système CLS (Common Language)-des types intégraux conformes, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, ou <xref:System.Int64> pour vous assurer que toutes les valeurs de l’énumération peuvent être représentées dans Langages de programmation conformes CLS.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, sauf si les problèmes de compatibilité ou de taille existent, utilisez <xref:System.Int32>. Pour les situations où <xref:System.Int32> n’est pas assez grand pour contenir les valeurs, utilisez <xref:System.Int64>. Si la compatibilité descendante requiert un type de données plus petits, utilisez <xref:System.Byte> ou <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle uniquement si des problèmes de compatibilité descendante le requièrent. Dans les applications, non-respect de cette règle généralement ne provoque pas de problèmes. Dans les bibliothèques, où l’interopérabilité des langages est requise, non-respect de cette règle peut nuire aux utilisateurs.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre deux énumérations qui n’utilisent pas le type de données sous-jacent recommandé.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Exemple de correctif

### <a name="description"></a>Description
 L’exemple suivant résout la violation précédente en modifiant le type de données sous-jacent <xref:System.Int32>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1008 : Les énumérations doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700 : Ne nommez pas les valeurs d’énumération 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712 : Ne préfixez pas les valeurs d’énumération avec le nom du type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>



