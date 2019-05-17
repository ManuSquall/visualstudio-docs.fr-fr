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
ms.openlocfilehash: 740ef26af6f1f84d23ef27de5176df1b3de98b34
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797326"
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

L’indice de maintenabilité est calculé en utilisant les métriques suivantes : lignes de code, volume de programme et complexité cyclomatique. Volume de programme est une mesure de la difficulté de compréhension d’un type ou une méthode qui est basé sur le nombre d’opérateurs et d’opérandes dans le code. Complexité cyclomatique est une mesure de la complexité structurelle du type ou de méthode. Plus d’informations sur la métrique du code à [mesurer la complexité et la maintenabilité du code managé](../code-quality/code-metrics-values.md).

Un faible indice de maintenabilité indique qu’un type ou une méthode est probablement difficile à maintenir et serait un bon candidat pour modifier la conception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour résoudre cette violation, reconcevez le type ou la méthode et essayez de diviser en plus petites et plus ciblées des types ou méthodes.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer cet avertissement lorsque le type de méthode ne peut pas être fractionnée ou est considéré comme plus facile à gérer en dépit de sa grande taille.

## <a name="see-also"></a>Voir aussi

- [Avertissements de la facilité de maintenance](../code-quality/maintainability-warnings.md)
- [Mesurer la complexité et la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)