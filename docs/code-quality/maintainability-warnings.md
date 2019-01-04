---
title: avertissements liés à la facilité de maintenance
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fc9b8be565cb7b8bad25b8bddbcb35158dcc0bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938660"
---
# <a name="maintainability-warnings"></a>avertissements liés à la facilité de maintenance

Avertissements de la facilité de gestion prennent en charge la gestion des bibliothèques et des applications.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
|-----------|-----------------------------------|
| [CA1500 : Les noms de variables ne doivent pas correspondre aux noms de champs](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant, ce qui entraîne des erreurs. |
| [CA1501 : Éviter l’excès d’héritage](../code-quality/ca1501-avoid-excessive-inheritance.md) | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| [CA1502 : Éviter l’excès de complexité](../code-quality/ca1502-avoid-excessive-complexity.md) | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| [CA1504 : Passez en revue les noms de champs trompeurs](../code-quality/ca1504-review-misleading-field-names.md) | Le nom d’un champ d’instance commence par « s_ » ou le nom de statique (partagé dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) champ commence par « m_ ». |
| [CA1505 : Éviter le code](../code-quality/ca1505-avoid-unmaintainable-code.md) | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| [CA1506 : Éviter les couplages de classe excessifs](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |

## <a name="see-also"></a>Voir aussi

- [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)