---
title: Afficher les travaux récents
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: a2970c0086ec18789347eebdea752487be18ce7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548391"
---
# <a name="view-recent-job-performance-and-details"></a>Afficher les détails et les performances des travaux récents

Une fois que les travaux sont envoyés, vous pouvez en afficher la liste pour voir leur état, leur durée et bien plus encore.

1. Dans **l’Explorateur de serveurs**, développez le contexte de calcul spécifique.
2. Double-cliquez sur **Travaux**.
3. La liste des travaux envoyés à ce contexte de calcul s’affiche.
4. Sélectionnez un **travail** spécifique dans la liste pour en afficher les détails.

![surveiller des travaux](media/job-details/monitor-jobs.png)

> L’historique des travaux envoyés aux machines virtuelles Linux est stocké sur la machine virtuelle dans le répertoire /tmp. Ainsi, à chaque redémarrage, l’historique des travaux est effacé. Pour conserver une trace de votre historique des travaux, configurez votre machine virtuelle en tant que contexte de calcul dans Azure Machine Learning, puis envoyez un travail à Azure Machine Learning (en sélectionnant votre machine virtuelle comme contexte de calcul).