---
title: "Vue Appelant/Appelé | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0792f59f02c5b75247d5066b132cf1072d37c76a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="callercallee-view"></a>Vue Appelant/Appelé
La vue Appelant/Appelé affiche des données de profilage pour la fonction sélectionnée, ainsi que pour ses fonctions parents et enfants. La vue Appelant/Appelé comprend trois grilles :  
  
 La grille centrale intitulée **Fonction active** contient les informations de profilage associées à la fonction sélectionnée. Les valeurs incluent tous les appels à la fonction qui ont été collectés lors de l’exécution du profilage.  
  
 La grille supérieure intitulée **Fonctions qui ont appelé la fonction active** indique le nombre correspondant aux valeurs de la fonction sélectionnée (active) qui ont été générées par les appels de la fonction d’appelant (parent).  
  
 La grille inférieure intitulée **Fonctions qui ont été appelées par la fonction active** contient des informations de profilage pour les fonctions d’appelé (enfants) de la fonction sélectionnée lorsque la fonction enfant a été appelée par la fonction active.  
  
 Les colonnes qui sont disponibles dans la vue Appelant/Appelé dépendent de la méthode de profilage (échantillonnage ou instrumentation) utilisée pour collecter les données, mais également de la présence de données de mémoire .NET parmi les données collectées lors de l’exécution du profilage.  
  
 Pour sélectionner une autre fonction comme fonction active, dans la grille centrale de la vue Rapport, double-cliquez sur l’une des fonctions répertoriées dans les deux autres grilles. La vue Rapport est mise à jour automatiquement pour refléter les modifications.  
  
 Vous pouvez trier les données en cliquant sur un nom de colonne. Des colonnes supplémentaires peuvent être ajoutées à la vue Appelant/Appelé. Pour plus d’informations, consultez [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Appelant/Appelé - Données d’échantillonnage](../profiling/caller-callee-view-sampling-data.md)   
 [Vue Appelant/Appelé - Données d’instrumentation](../profiling/caller-callee-view-instrumentation-data.md)   
 [Vue Appelant/Appelé - Données d’instrumentation de la mémoire .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vue Appelant/Appelé - Données d’échantillonnage de mémoire .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vue Appelant/Appelé - Données de conflit](../profiling/caller-callee-view-contention-data.md)