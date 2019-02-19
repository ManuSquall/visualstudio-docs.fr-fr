---
title: Contrôle de la collecte de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780945"
---
# <a name="controlling-data-collection"></a>Contrôle de la collecte de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permettent de choisir à quel moment les données de profilage doivent être collectées pendant une session de performance, et permettent de spécifier les fonctions profilées. Cette section explique comment démarrer et arrêter la collecte de données à partir des fenêtres **Explorateur de performances** et **Contrôle de collecte de données**, et comment limiter les objets pour lesquels les données de profilage sont collectées.  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu associé|  
|----------|---------------------|  
|**Démarrer et arrêter le profilage** : vous pouvez démarrer le profilage d’une application à son démarrage, ou vous pouvez attacher le profileur à un processus en cours d’exécution. Lorsque l’application cible s’exécute, vous pouvez suspendre et reprendre la collecte des données. Pour arrêter une session de profilage, fermez l’application cible ou détachez le profileur du processus en cours d’exécution.|-   [Guide pratique pour démarrer et terminer la collecte des données de performances](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Guide pratique pour attacher les outils d’analyse des performances à des processus en cours d’exécution ou les en détacher](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Guide pratique pour suspendre et reprendre la collecte de données de performances](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Configurer le profilage par instrumentation pour limiter les données collectées** : vous pouvez utiliser les propriétés de configuration de la session de performance pour limiter les données collectées lors des exécutions de profilage qui utilisent la méthode d’instrumentation. Vous pouvez inclure ou exclure des fichiers .dll, des espaces de noms, des classes et des fonctions spécifiques. Vous pouvez également exclure les fonctions dont la taille ne respecte pas le seuil que vous avez spécifié.|-   [Guide pratique pour limiter l’instrumentation à des DLL spécifiques](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Guide pratique pour limiter l’instrumentation à des fonctions spécifiques](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Guide pratique pour exclure ou inclure les fonctions courtes dans l’instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de performances](../profiling/performance-explorer.md)
