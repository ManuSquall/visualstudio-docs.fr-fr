---
title: 'CA1712 : N’ajoutez pas de préfixe valeurs enum avec le nom de type | Microsoft Docs'
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
ms.openlocfilehash: 9283c35dacc0d3f3779a167eeb095f90431d7a4c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589751"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1712 : n’ajoutez pas de valeurs d’énumération avec le nom de type préfixe](https://docs.microsoft.com/visualstudio/code-quality/ca1712-do-not-prefix-enum-values-with-type-name).

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

 Conventions d’affectation de noms fournissent une apparence commune pour les bibliothèques qui ciblent le common language runtime. Cela réduit le temps nécessaire pour apprendre une nouvelle bibliothèque de logiciels, et augmente la confiance des clients que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.

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
 [CA1711 : Les identificateurs ne doivent pas avoir un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Enum?displayProperty=fullName>



