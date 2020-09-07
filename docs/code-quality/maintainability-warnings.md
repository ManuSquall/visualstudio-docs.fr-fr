---
title: avertissements liés à la facilité de maintenance
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb985a6482b76b79604ce58f85e7f8cf3e83e97c
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509898"
---
# <a name="maintainability-warnings"></a>Avertissements liés à la maintenabilité

Les avertissements de maintenabilité prennent en charge la gestion des bibliothèques et des applications.

## <a name="in-this-section"></a>Contenu de cette section

| Règle | Description |
|-----------|-----------------------------------|
| [CA1501 : Éviter l'excès d'héritage](../code-quality/ca1501.md) | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| [CA1502 : Éviter l'excès de complexité](../code-quality/ca1502.md) | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| [CA1505 : Éviter le code impossible à maintenir](../code-quality/ca1505.md) | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| [CA1506 : Éviter les couplages de classe excessifs](../code-quality/ca1506.md) | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |
| [CA1507 : Utiliser nameof à la place de string](../code-quality/ca1507.md) | Un littéral de chaîne est utilisé en tant qu’argument dans lequel une `nameof` expression peut être utilisée. |
| [CA1508 : Éviter le code conditionnel mort](../code-quality/ca1508.md) | Une méthode a un code conditionnel qui prend toujours la valeur `true` ou `false` au moment de l’exécution. Cela provoque un code mort dans la `false` branche de la condition. |
| [CA1509 : Entrée non valide dans le fichier de configuration des métriques de code](../code-quality/ca1509.md) | Les règles de métrique du code, telles que [CA1501](ca1501.md), [CA1502](ca1502.md), [ca1505](ca1505.md) et [CA1506](ca1506.md), ont fourni un fichier de configuration nommé `CodeMetricsConfig.txt` qui a une entrée non valide. |

## <a name="see-also"></a>Voir aussi

- [Mesure de la complexité et de la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)
