---
title: 'CA1506 : Éviter les couplages de classe excessifs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8d2e85ebacdedfde9d6731ff3e24a557de3e13
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988554"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506 : Éviter les couplages de classe excessifs

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type ou une méthode est associée à d’autres types.

## <a name="rule-description"></a>Description de la règle
 Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.

 Types et méthodes qui présentent un degré élevé de couplage de classe peuvent être difficiles à gérer. Il est judicieux d’avoir des types et méthodes qui présentent un couplage faible et une forte cohésion.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, essayez de redéfinir le type ou la méthode pour réduire le nombre de types auquel il est associé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Exclure cet avertissement lors de la méthode ou le type est considéré comme plus facile à gérer en dépit de son grand nombre de dépendances sur d’autres types.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la facilité de maintenance](../code-quality/maintainability-warnings.md)
- [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)