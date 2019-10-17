---
title: 'CA1505 : Éviter le code impossible à maintenir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f39b6b909722c35edb16ebaf1cee43507f22215d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440073"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505 : Éviter le code impossible à maintenir

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type ou une méthode a une faible valeur d'indice de maintenabilité.

## <a name="rule-description"></a>Description de la règle

L’index de maintenabilité est calculé à l’aide des métriques suivantes : lignes de code, volume de programme et complexité cyclomatic. Le volume de programme est une mesure de la difficulté de comprendre un type ou une méthode basée sur le nombre d’opérateurs et d’opérandes dans le code. La complexité cyclomatic est une mesure de la complexité structurelle du type ou de la méthode. Vous pouvez en savoir plus sur les métriques [du code à mesure que la complexité et la facilité de maintenance du code managé](../code-quality/code-metrics-values.md).

Un index de maintenabilité faible indique qu’un type ou une méthode est probablement difficile à gérer et qu’il s’agit d’un bon candidat pour la reconception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger cette violation, reconcevez le type ou la méthode et essayez de le fractionner en types ou méthodes plus petits et plus ciblés.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer cet avertissement lorsque le type ou la méthode ne peut pas être fractionné ou est considéré comme gérable en dépit de sa grande taille.

## <a name="see-also"></a>Voir aussi

- [Avertissements de maintenabilité](../code-quality/maintainability-warnings.md)
- [Mesurer la complexité et la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)
