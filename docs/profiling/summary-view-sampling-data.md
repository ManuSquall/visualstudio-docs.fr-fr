---
title: Vue Résumé - Données d’échantillonnage | Microsoft Docs
description: Découvrez comment le mode Résumé affiche des informations sur les fonctions les plus coûteuses en matière de performances dans une exécution de profilage.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e5d75574e29118beacb6312d2dd013a19894a176
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718952"
---
# <a name="summary-view---sampling-data"></a>Vue Résumé - Données d’échantillonnage
La vue Résumé affiche des informations sur les fonctions dont le coût est le plus élevé quant aux performances dans une exécution du profilage. Pour plus d’informations, notamment une description des liens de notification et des listes de rapports, consultez [Vue Résumé](../profiling/summary-view.md).

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="timeline-graph"></a>Graphique chronologique
 Le graphique chronologique de la vue Résumé montre le pourcentage d’utilisation du processeur (UC) de l’application profilée pendant la durée du profilage. Vous pouvez utiliser le graphique chronologique pour filtrer la vue en lui appliquant un intervalle de temps sélectionné. Pour plus d’informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Chemin réactif
 Le **chemin réactif** montre le chemin d’exécution dans lequel la plupart des échantillons ont été collectés. Vous pouvez cliquer sur une fonction pour afficher la vue Détails de la fonction pour celle-ci. Pour afficher d’autres vues pour la fonction, cliquez avec le bouton droit sur la fonction puis cliquez sur une vue de la liste.

 Le **chemin réactif** inclut les données suivantes pour chaque fonction :

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom de la fonction.|
|**% des échantillons inclusifs**|Pourcentage de tous les échantillons collectés quand cette fonction ou une fonction appelée par cette fonction s’exécutait.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons collectés quand la fonction exécutait du code du corps de la fonction. Ce pourcentage n’inclut pas les échantillons collectés dans les fonctions appelées par cette fonction.|

## <a name="functions-doing-most-individual-work"></a>Fonctions faisant le plus de travail individuel
 La liste **Fonctions faisant le plus de travail individuel** montre les fonctions qui ont le plus grand nombre d’échantillons exclusifs dans l’exécution du profilage. Un échantillon exclusif est affecté à une fonction si la fonction exécutait son propre code quand l’échantillon a été collecté. Un échantillon exclusif n’est pas affecté à une fonction si la fonction appelait une autre fonction quand l’échantillon a été collecté. Un grand nombre d’échantillons exclusifs indique qu’un temps considérable a été passé dans la fonction elle-même.

 Vous pouvez cliquer sur une fonction pour afficher la vue Détails de la fonction pour celle-ci. Pour afficher d’autres vues pour la fonction, cliquez avec le bouton droit sur la fonction, puis cliquez sur une vue de la liste.

 **Fonctions faisant plus de travail individuel** inclut les données suivantes pour chaque fonction :

|Colonne|Description|
|------------|-----------------|
|**Nom**|Nom de la fonction.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution de la fonction collectés quand la fonction exécutait du code du corps de la fonction. Le pourcentage ne comprend pas les échantillons collectés quand des fonctions appelées par cette fonction étaient en cours d’exécution.|

## <a name="see-also"></a>Voir aussi
- [Vue Résumé - Données de la mémoire .NET](../profiling/summary-view-dotnet-memory-data.md)
- [Vue Résumé-données d’instrumentation](../profiling/summary-view-instrumentation-data.md)
