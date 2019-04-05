---
title: 'CA1712 : N’ajoutez pas de valeurs d’énumération avec le nom de type préfixe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 19b64c0d7c45bb2425ca3e59bd56f5c251feef50
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938691"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une énumération contient un membre dont le nom commence par le nom de type de l’énumération.

## <a name="rule-description"></a>Description de la règle
 Noms des membres de l’énumération ne sont pas préfixés par le nom de type, car les informations de type sont censées être fournis par les outils de développement.

 Les conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels, et augmente la confiance des clients que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le préfixe de nom de type du membre d’énumération.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une énumération incorrectement nommée suivie de la version corrigée.

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne pas marquer les enums avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Enum?displayProperty=fullName>
