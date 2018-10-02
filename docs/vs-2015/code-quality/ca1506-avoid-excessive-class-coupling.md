---
title: 'CA1506 : Éviter les couplages de classe excessifs | Microsoft Docs'
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
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a2f96701ccecdd5e3859dcc434a748200f7fd784
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588011"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506 : Éviter les couplages de classe excessifs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1506 : éviter les couplages de classe excessifs](https://docs.microsoft.com/visualstudio/code-quality/ca1506-avoid-excessive-class-coupling).

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
 [Avertissements de la facilité de maintenance](../code-quality/maintainability-warnings.md) [mesure la complexité et la maintenabilité du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



