---
title: 'CA1506 : Éviter les couplages de classe excessifs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234496"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506 : Éviter les couplages de classe excessifs

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type ou une méthode est associé à de nombreux autres types.

## <a name="rule-description"></a>Description de la règle

Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.

Les types et les méthodes qui ont un haut degré de couplage de classe peuvent être difficiles à gérer. Il est recommandé d’avoir des types et des méthodes qui présentent un couplage faible et une cohésion élevée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour résoudre ce problème, essayez de reconcevoir le type ou la méthode afin de réduire le nombre de types auxquels il est associé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Excluez cet avertissement lorsque le type ou la méthode est considéré comme gérable en dépit de son grand nombre de dépendances sur d’autres types.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la facilité de maintenance](../code-quality/maintainability-warnings.md)
- [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)