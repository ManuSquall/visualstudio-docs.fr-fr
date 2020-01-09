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
ms.openlocfilehash: 5dad282bfc1c539216b55e41d77d7743808311d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587366"
---
# <a name="maintainability-warnings"></a>Avertissements liés à la maintenabilité

Les avertissements de maintenabilité prennent en charge la gestion des bibliothèques et des applications.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
|-----------|-----------------------------------|
| [CA1500 : Les noms de variable ne doivent pas être identiques à des noms de champs](../code-quality/ca1500.md) | Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant, ce qui génère des erreurs. |
| [CA1501 : Évitez l’excès d’héritage](../code-quality/ca1501.md) | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| [CA1502 : Éviter une complexité excessive](../code-quality/ca1502.md) | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| [CA1504 : Vérifiez les noms de champs peu clairs](../code-quality/ca1504.md) | Le nom d’un champ d’instance commence par « s_ », ou le nom d’un champ statique (partagé dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) commence par « m_ ». |
| [CA1505 : Évitez le code impossible à maintenir](../code-quality/ca1505.md) | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| [CA1506 : Évitez les couplages de classe excessifs](../code-quality/ca1506.md) | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |
| [Ca1507 : utiliser nameof à la place de String](../code-quality/ca1507.md) | Un littéral de chaîne est utilisé en tant qu’argument dans lequel une expression `nameof` peut être utilisée. |

## <a name="see-also"></a>Voir aussi

- [Mesure de la complexité et de la facilité de maintenance du code managé](../code-quality/code-metrics-values.md)
