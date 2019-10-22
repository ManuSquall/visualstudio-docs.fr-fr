---
title: 'CA1506 : éviter un couplage de classe excessif | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e85ac61e404ac9bc1afb9459716c2395233c5080
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607407"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506 : Éviter les couplages de classe excessifs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type ou une méthode est associé à de nombreux autres types.

## <a name="rule-description"></a>Description de la règle
 Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.

 Les types et les méthodes qui ont un haut degré de couplage de classe peuvent être difficiles à gérer. Il est recommandé d’avoir des types et des méthodes qui présentent un couplage faible et une cohésion élevée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger cette violation, essayez de reconcevoir le type ou la méthode afin de réduire le nombre de types auxquels il est couplé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Excluez cet avertissement lorsque le type ou la méthode est encore considéré comme gérable en dépit de son grand nombre de dépendances sur d’autres types.

## <a name="see-also"></a>Voir aussi
 [Avertissements de maintenabilité](../code-quality/maintainability-warnings.md) [mesure de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
