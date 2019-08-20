---
title: Vue Modules | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d396aec92b43aebca9b398c6d481962138354e0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195613"
---
# <a name="modules-view"></a>Vue Modules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue Modules liste les modules des données de profilage. Chaque module est le nœud racine d’une arborescence hiérarchique. Les fonctions profilées du module sont répertoriées sous le nœud du module. Si les données de profilage ont été collectées avec la méthode d’échantillonnage, les informations de ligne figurent sous le nœud de fonction et les données de pointeur d’instruction sont répertoriées sous le nœud de ligne.  
  
 Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module.  
  
 Pour ajouter ou supprimer des colonnes, cliquez avec le bouton droit dans la fenêtre du rapport, puis sélectionnez **Ajouter/Supprimer des colonnes**. Vous pouvez trier les données en cliquant sur un nom de colonne. Pour plus d'informations, voir [Procédure : Personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md).  
  
 Les colonnes qui sont disponibles dans la vue Modules dépendent de la méthode de profilage (échantillonnage ou instrumentation) utilisée pour collecter les données, mais également de la présence de données de mémoire .NET parmi les données collectées lors de l’exécution du profilage.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Modules - Données d’instrumentation](../profiling/modules-view-sampling-data.md)   
 [Vue Modules - Données d’instrumentation](../profiling/modules-view-instrumentation-data.md)   
 [Modules, vue - Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vue Modules - Échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modules, mode](../profiling/modules-view-contention-data.md)
