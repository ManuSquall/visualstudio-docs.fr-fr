---
title: Afficher les tâches récentes
description: Pour savoir qu’une fois les travaux envoyés, vous pouvez afficher la liste des travaux pour afficher leur état, leur durée et bien plus encore.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 13d78913e0d5d708c5e75a80611ae9cc1c2f7366
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841430"
---
# <a name="view-recent-job-performance-and-details"></a>Afficher les détails et les performances des travaux récents

Une fois que les travaux sont envoyés, vous pouvez en afficher la liste pour voir leur état, leur durée et bien plus encore.

1. Dans le **Explorateur de serveurs**, développez le contexte de calcul spécifique.
2. Double-cliquez sur **Travaux**.
3. La liste des travaux envoyés à ce contexte de calcul s’affiche.
4. Sélectionnez un **travail** spécifique dans la liste pour en afficher les détails.

![surveiller des travaux](media/job-details/monitor-jobs.png)

> L’historique des travaux envoyés aux machines virtuelles Linux est stocké sur la machine virtuelle dans le répertoire /tmp. Ainsi, à chaque redémarrage, l’historique des travaux est effacé. Pour conserver une trace de votre historique des travaux, configurez votre machine virtuelle en tant que contexte de calcul dans Azure Machine Learning, puis envoyez un travail à Azure Machine Learning (en sélectionnant votre machine virtuelle comme contexte de calcul).
