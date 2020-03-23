---
title: Afficher les tâches récentes
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 79b396946666077dcdedb3ee2a5ab891c2bb4fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777394"
---
# <a name="view-recent-job-performance-and-details"></a>Afficher les détails et les performances des travaux récents

Une fois que les travaux sont envoyés, vous pouvez en afficher la liste pour voir leur état, leur durée et bien plus encore.

1. Dans le **Server Explorer**, élargir le contexte de calcul spécifique.
2. Double-cliquez sur **Travaux**.
3. La liste des travaux envoyés à ce contexte de calcul s’affiche.
4. Sélectionnez un **emploi** spécifique dans la liste pour afficher les détails.

![surveiller des travaux](media/job-details/monitor-jobs.png)

> L’historique des travaux envoyés aux machines virtuelles Linux est stocké sur la machine virtuelle dans le répertoire /tmp. Ainsi, à chaque redémarrage, l’historique des travaux est effacé. Pour conserver une trace de votre historique des travaux, configurez votre machine virtuelle en tant que contexte de calcul dans Azure Machine Learning, puis envoyez un travail à Azure Machine Learning (en sélectionnant votre machine virtuelle comme contexte de calcul).
