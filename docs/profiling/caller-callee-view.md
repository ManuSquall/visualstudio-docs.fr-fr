---
title: Vue Appelant/Appelé | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a6a994f5ff564860ac753787eebd293a8e2fa9c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889731"
---
# <a name="callercallee-view"></a>mode Appelant/Appelé
La vue Appelant/Appelé affiche des données de profilage pour la fonction sélectionnée, ainsi que pour ses fonctions parents et enfants. La vue Appelant/Appelé comprend trois grilles :

 La grille centrale intitulée **Fonction active** contient les informations de profilage associées à la fonction sélectionnée. Les valeurs incluent tous les appels à la fonction qui ont été collectés lors de l’exécution du profilage.

 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** indique le nombre correspondant aux valeurs de la fonction sélectionnée (active) qui ont été générées par les appels de la fonction d’appelant (parent).

 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient des informations de profilage pour les fonctions d’appelé (enfants) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.

 Les colonnes qui sont disponibles dans la vue Appelant/Appelé dépendent de la méthode de profilage (échantillonnage ou instrumentation) utilisée pour collecter les données, mais également de la présence de données de mémoire .NET parmi les données collectées lors de l’exécution du profilage.

 Pour sélectionner une autre fonction comme fonction active, dans la grille centrale de la vue Rapport, double-cliquez sur l’une des fonctions répertoriées dans les deux autres grilles. La vue Rapport est mise à jour automatiquement pour refléter les modifications.

 Vous pouvez trier les données en cliquant sur un nom de colonne. Des colonnes supplémentaires peuvent être ajoutées à la vue Appelant/Appelé. Pour plus d’informations, consultez [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Voir aussi
- [Vue Appelant/Appelé - Données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)
- [Vue appelant/appelé-données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)
- [Vue appelant/appelé-données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Vue appelant/appelé-données d’échantillonnage de la mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Vue Appelant/Appelé - Données de conflit](../profiling/caller-callee-view-contention-data.md)
