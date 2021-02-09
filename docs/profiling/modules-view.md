---
title: Vue Modules | Microsoft Docs
description: Découvrez comment la vue modules répertorie les modules des données de profilage. Chaque module est le nœud racine d’une arborescence hiérarchique.
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 412b40fdb38e4931bcefb05bde8d695955d6c05a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879733"
---
# <a name="modules-view"></a>Vue Modules
La vue Modules liste les modules des données de profilage. Chaque module est le nœud racine d’une arborescence hiérarchique. Les fonctions profilées du module sont répertoriées sous le nœud du module. Si les données de profilage ont été collectées avec la méthode d’échantillonnage, les informations de ligne figurent sous le nœud de fonction et les données de pointeur d’instruction sont répertoriées sous le nœud de ligne.

 Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module.

 Pour ajouter ou supprimer des colonnes, cliquez avec le bouton droit dans la fenêtre du rapport, puis sélectionnez **Ajouter/supprimer des colonnes**. Vous pouvez trier les données en cliquant sur un nom de colonne. Pour plus d’informations, consultez [Comment : personnaliser les colonnes de la vue rapport](../profiling/how-to-customize-report-view-columns.md).

 Les colonnes qui sont disponibles dans la vue Modules dépendent de la méthode de profilage (échantillonnage ou instrumentation) utilisée pour collecter les données, mais également de la présence de données de mémoire .NET parmi les données collectées lors de l’exécution du profilage.

## <a name="see-also"></a>Voir aussi
- [Vue Modules](../profiling/modules-view-sampling-data.md)
- [Vue Modules](../profiling/modules-view-instrumentation-data.md)
- [Vue modules-Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Vue modules-échantillonnage](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Vue Modules](../profiling/modules-view-contention-data.md)
