---
title: Vue Modules | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 89d9146b3f724b4883f21a43689a495eef252777
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778516"
---
# <a name="modules-view"></a>Vue Modules
La vue Modules liste les modules des données de profilage. Chaque module est le nœud racine d’une arborescence hiérarchique. Les fonctions profilées du module sont répertoriées sous le nœud du module. Si les données de profilage ont été collectées avec la méthode d’échantillonnage, les informations de ligne figurent sous le nœud de fonction et les données de pointeur d’instruction sont répertoriées sous le nœud de ligne.

 Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module.

 Pour ajouter ou supprimer des colonnes, cliquez à droite dans la fenêtre du rapport, puis sélectionnez **Ajouter/Supprimer les colonnes**. Vous pouvez trier les données en cliquant sur un nom de colonne. Pour plus d’informations, voir [Comment personnaliser les colonnes De vue de rapport](../profiling/how-to-customize-report-view-columns.md).

 Les colonnes qui sont disponibles dans la vue Modules dépendent de la méthode de profilage (échantillonnage ou instrumentation) utilisée pour collecter les données, mais également de la présence de données de mémoire .NET parmi les données collectées lors de l’exécution du profilage.

## <a name="see-also"></a>Voir aussi
- [Vue Modules](../profiling/modules-view-sampling-data.md)
- [Vue Modules](../profiling/modules-view-instrumentation-data.md)
- [Modules Vue - instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modules Vue - échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Vue Modules](../profiling/modules-view-contention-data.md)
