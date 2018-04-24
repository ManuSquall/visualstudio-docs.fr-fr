---
title: Règles de performance de mémoire et de pagination
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7949f19198aebe37b4a846cc37f274940415fb8e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="memory-and-paging-performance-rules"></a>Règles de performance de mémoire et de pagination
Les règles de performance de la catégorie mémoire et pagination identifient l’activité de pagination lors d’une exécution du profilage, qui peut affecter les performances et la réactivité de l’application.  
  
|||  
|-|-|  
|[DA0014 : Taux très élevés de pagination de la mémoire active sur le disque](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Un taux très élevé de pagination de la mémoire active vers et depuis le disque s’est produit au cours de l’exécution du profilage. Un tel taux de pagination affecte généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Essayez en réexécutant le profilage sur un ordinateur disposant de plus de mémoire. Cette règle se déclenche quand la quantité d’activité de pagination dépasse le seuil supérieur de la règle D0017.|  
|[DA0017 : Taux élevés de pagination de la mémoire active sur le disque](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Un taux relativement élevé de pagination de la mémoire active vers et depuis le disque s’est produit au cours de l’exécution du profilage. Un tel taux de pagination affecte généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Essayez en réexécutant le profilage sur un ordinateur disposant de plus de mémoire.|