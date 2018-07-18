---
title: 'CA1505 : Éviter le code impossible à maintenir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41600d40091ed2c656ab189a257a0ef2db6e0271
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914404"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505 : Éviter le code impossible à maintenir
|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type ou une méthode a une faible valeur d'indice de maintenabilité.

## <a name="rule-description"></a>Description de la règle
 L’indice de maintenabilité est calculé en utilisant les métriques suivantes : lignes de code, le volume de programme et la complexité cyclomatique. Volume de programme est une mesure de la difficulté de présentation d’un type ou une méthode qui est basé sur le nombre d’opérateurs et d’opérandes dans le code. La complexité cyclomatique est une mesure de la complexité structurelle du type ou de méthode. Plus d’informations sur la métrique du code à [mesure la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un faible indice de maintenabilité indique qu’un type ou une méthode est probablement difficile à maintenir et qu’un bon candidat pour modifier la conception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, reconcevez le type ou la méthode et essayez de fractionner en plus petites et plus ciblés des types ou des méthodes.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Exclure cet avertissement lorsqu’un type ou une méthode est considéré comme facile à maintenir en dépit de sa grande taille ou de la méthode ou le type ne peut pas être fractionnée.

## <a name="see-also"></a>Voir aussi
 [Avertissements de facilité de maintenance](../code-quality/maintainability-warnings.md) [mesure la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)