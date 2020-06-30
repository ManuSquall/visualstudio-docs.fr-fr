---
title: 'Ca1505 : éviter le code impossible à maintenir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f2f731b1ac0d87b59c7690d0cf57ade3570ed5f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547821"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505 : Éviter le code impossible à maintenir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type ou une méthode a une faible valeur d'indice de maintenabilité.

## <a name="rule-description"></a>Description de la règle
 L’index de maintenabilité est calculé à l’aide des métriques suivantes : lignes de code, volume de programme et complexité cyclomatic. Le volume de programme est une mesure de la difficulté de comprendre un type ou une méthode basée sur le nombre d’opérateurs et d’opérandes dans le code. La complexité cyclomatic est une mesure de la complexité structurelle du type ou de la méthode. Vous pouvez en savoir plus sur les métriques [du code pour mesurer la complexité et la maintenabilité du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un index de maintenabilité faible indique qu’un type ou une méthode est probablement difficile à gérer et qu’il s’agit d’un bon candidat pour la reconception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger cette violation, reconcevez le type ou la méthode et essayez de le fractionner en types ou méthodes plus petits et plus ciblés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Excluez cet avertissement lorsqu’un type ou une méthode est toujours considéré comme gérable en dépit de sa grande taille ou lorsque le type ou la méthode ne peut pas être fractionné.

## <a name="see-also"></a>Voir aussi
 [Avertissements de maintenabilité](../code-quality/maintainability-warnings.md) [mesure de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
