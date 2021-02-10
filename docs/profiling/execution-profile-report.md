---
title: Profil d’exécution, rapport| Microsoft Docs
description: En savoir plus sur le rapport de profil d’exécution, qui est un profil d’échantillonnage traditionnel dans l’extension du visualiseur concurrentiel pour Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7a61e3a9ba159977d4a835126b2a584be1597c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955253"
---
# <a name="execution-profile-report"></a>Profil d’exécution, rapport
Le rapport Profil d’exécution est un profil d’échantillonnage classique. Des échantillons sont créés chaque milliseconde environ pendant des périodes où un thread s’exécute sur un cœur logique, et le visualiseur concurrentiel génère une arborescence des appels typique en assemblant les échantillons de piles accumulés. Les données de ce tableau peuvent être affectées par la plage horaire actuelle et les threads cachés, ainsi que par les filtres qui peuvent être appliqués :

- Si l’option Uniquement mon code est activée, seuls les frames de pile contenant du code utilisateur sont présentés, ainsi que le premier niveau situé sous le code utilisateur.

- Si la valeur Réduction du bruit est définie, les piles assemblées dont la fréquence est inférieure à celle spécifiée sont retirées du rapport.

  Le tableau suivant montre les colonnes du rapport.

|Colonne|Description|
|------------|-----------------|
|Nom|Nom de la fonction pour chaque niveau de la pile des appels.|
|Échantillons inclusifs|Nombre total d’échantillons collectés pour toutes les piles qui atteignent ce niveau de l’arborescence de la pile des appels. Le nombre inclusif correspond à la somme des échantillons exclusifs de cette fonction et des compteurs inclusifs de tous ses nœuds enfants.|
|Exemples exclusifs|Nombre total d’échantillons collectés pour lesquels cette fonction correspond au niveau le plus bas de la pile des appels.|
|% inclusif|Pourcentage du total des échantillons qui apparaissent dans la colonne des échantillons inclusifs. Les pourcentages sont arrondis à deux décimales.|
|% exclusifs|Pourcentage du total des échantillons qui apparaissent dans la colonne des échantillons exclusifs. Les pourcentages sont arrondis à deux décimales.|
|Détails|Nom complet de la fonction. Peut contenir le nombre de lignes lorsque celui-ci est disponible.|

 Cette table de rapport peut être affichée dans la vue [durée d’exécution (vue threads)](../profiling/execution-time-threads-view.md) .

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)