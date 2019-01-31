---
title: Afficher les tâches récentes
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: b51f6d72455e455f8be5177fc99987eb703d7e94
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801880"
---
# <a name="view-recent-job-performance-and-details"></a>Afficher les détails et les performances des travaux récents

Une fois que les travaux sont envoyés, vous pouvez en afficher la liste pour voir leur état, leur durée et bien plus encore.

1. Dans **l’Explorateur de serveurs**, développez le contexte de calcul spécifique.
2. Double-cliquez sur **Travaux**.
3. La liste des travaux envoyés à ce contexte de calcul s’affiche.
4. Sélectionnez un **travail** spécifique dans la liste pour en afficher les détails.

![surveiller des travaux](media/job-details/monitor-jobs.png)

> L’historique des travaux envoyés aux machines virtuelles Linux est stocké sur la machine virtuelle dans le répertoire /tmp. Ainsi, à chaque redémarrage, l’historique des travaux est effacé. Pour conserver une trace de votre historique des travaux, configurez votre machine virtuelle en tant que contexte de calcul dans Azure Machine Learning, puis envoyez un travail à Azure Machine Learning (en sélectionnant votre machine virtuelle comme contexte de calcul).