---
title: 'CA1506 : Éviter les couplages de classe excessifs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: a613ecfd339399b161292a75f7fb2abeb972d986
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916675"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506 : Éviter les couplages de classe excessifs
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

 Types et méthodes qui présentent un degré élevé de couplage de classe peuvent être difficiles à maintenir. Il est judicieux d’avoir des types et méthodes qui présentent le couplage faible et une cohésion élevée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, essayez de reconcevoir le type ou la méthode pour réduire le nombre de types auxquels elle est associée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Exclure cet avertissement lors de la méthode ou le type est considéré comme facile à maintenir en dépit de son grand nombre de dépendances sur d’autres types.

## <a name="see-also"></a>Voir aussi
 [Avertissements de facilité de maintenance](../code-quality/maintainability-warnings.md) [mesure la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)