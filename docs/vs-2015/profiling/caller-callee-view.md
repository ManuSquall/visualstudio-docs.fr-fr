---
title: Vue Appelant/Appelé | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 37
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a28f0184d126781c43540d447cd75cd905e15d40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495422"
---
# <a name="callercallee-view"></a>Appelant/Appelé, mode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue appelant / appelé](https://docs.microsoft.com/visualstudio/profiling/caller-callee-view).  
  
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



