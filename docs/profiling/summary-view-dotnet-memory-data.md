---
title: Vue Résumé - Données de la mémoire .NET | Microsoft Docs
description: Découvrez comment le mode Résumé affiche des informations sur les fonctions et les types .NET qui ont alloué le plus de mémoire.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6aa2daf8e03f61d529f0d07c8f78af49821fa92b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960011"
---
# <a name="summary-view---net-memory-data"></a>Vue Résumé - Données de la mémoire .NET
La vue Résumé affiche des informations sur les fonctions et les types .NET qui ont alloué le plus de mémoire, et sur les types qui ont été créés le plus grand nombre de fois dans une exécution du profilage. Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [vue Résumé](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Graphique chronologique
 Le graphique chronologique de la vue Résumé montre l’utilisation du processeur (UC) par application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d’informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Fonctions allouant le plus de mémoire
 Répertorie les fonctions qui ont alloué le plus grand nombre d’octets de mémoire dans l’exécution du profilage.

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom de la fonction.|
|**% d’octets**|Pourcentage de tous les octets alloués dans l’exécution du profilage qui ont été alloués par cette fonction ou par une fonction enfant qui a été appelée par cette fonction.|

## <a name="types-with-most-memory-allocated"></a>Types ayant le plus de mémoire allouée
 Répertorie les types pour lesquels le plus grand nombre d’octets de mémoire ont été alloués dans l’exécution du profilage.

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom du type.|
|**% d’octets**|Pourcentage de tous les octets alloués dans l’exécution du profilage qui ont été alloués pour ce type.|

## <a name="types-with-most-instances"></a>Types ayant le plus d’instances
 Répertorie les types qui ont été créés le plus grand nombre de fois au cours de l’exécution du profilage. a

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom du type.|
|**% d’instances**|Pourcentage du nombre total d’objets .NET créés dans l’exécution du profilage et qui étaient des instances de ce type.|

## <a name="see-also"></a>Voir aussi
- [Vue Résumé-données d’échantillonnage](../profiling/summary-view-sampling-data.md)
- [Vue Résumé-données d’instrumentation](../profiling/summary-view-instrumentation-data.md)
