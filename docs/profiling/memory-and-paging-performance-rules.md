---
title: Règles de performance de mémoire et de pagination
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f779a050c334e8f61d6d3711ed2be2a7b087e72
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640036"
---
# <a name="memory-and-paging-performance-rules"></a>Règles de performance de mémoire et de pagination
Les règles de performance de la catégorie mémoire et pagination identifient l’activité de pagination lors d’une exécution du profilage, qui peut affecter les performances et la réactivité de l’application.

|||
|-|-|
|[DA0014 : taux très élevés de pagination de la mémoire active sur le disque](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Un taux très élevé de pagination de la mémoire active vers et depuis le disque s’est produit au cours de l’exécution du profilage. Un tel taux de pagination affecte généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Essayez en réexécutant le profilage sur un ordinateur disposant de plus de mémoire. Cette règle se déclenche quand la quantité d’activité de pagination dépasse le seuil supérieur de la règle D0017.|
|[DA0017 : taux élevés de pagination de la mémoire active sur le disque](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Un taux relativement élevé de pagination de la mémoire active vers et depuis le disque s’est produit au cours de l’exécution du profilage. Un tel taux de pagination affecte généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Essayez en réexécutant le profilage sur un ordinateur disposant de plus de mémoire.|