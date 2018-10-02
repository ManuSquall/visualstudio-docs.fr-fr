---
title: Règles de performance de mémoire et de pagination
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e9512fefc13dccebdb0a930ea6000edcbbd8f7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495081"
---
# <a name="memory-and-paging-performance-rules"></a>Règles de performance de mémoire et de pagination
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [mémoire et pagination des règles de performances](https://docs.microsoft.com/visualstudio/profiling/memory-and-paging-performance-rules).  
  
Les règles de performance de la catégorie mémoire et pagination identifient l’activité de pagination lors d’une exécution du profilage, qui peut affecter les performances et la réactivité de l’application.  
  
|||  
|-|-|  
|[DA0014 : Taux très élevés de pagination de la mémoire active sur le disque](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Un taux très élevé de pagination de la mémoire active vers et depuis le disque s’est produit au cours de l’exécution du profilage. Un tel taux de pagination affecte généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Essayez en réexécutant le profilage sur un ordinateur disposant de plus de mémoire. Cette règle se déclenche quand la quantité d’activité de pagination dépasse le seuil supérieur de la règle D0017.|  
|[DA0017 : Taux élevés de pagination de la mémoire active sur le disque](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Un taux relativement élevé de pagination de la mémoire active vers et depuis le disque s’est produit au cours de l’exécution du profilage. Un tel taux de pagination affecte généralement les performances et la réactivité de l’application. Réduisez les allocations de mémoire en modifiant les algorithmes. Envisagez également de revoir les besoins en mémoire de votre application. Essayez en réexécutant le profilage sur un ordinateur disposant de plus de mémoire.|



