---
title: "Collecte de données d’interaction de couche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3c586b027bec7e480b3dc3b2b378b0ce9600a7d4
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="collecting-tier-interaction-data"></a>Collecte de données d’interaction de couche

Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des fonctions d’applications multicouches qui communiquent avec des bases de données via les services ADO.NET. Les données sont collectées uniquement pour les appels de fonctions synchrones.

**Éditions Visual Studio**

Pour collecter des données de profilage d’interaction de couche, vous pouvez utiliser n’importe quelle édition de Visual Studio. Cependant, ces données ne sont consultables que dans Visual Studio Enterprise.

**Windows 8 et Windows Server 2012**

Pour collecter des données d’interaction de couche à partir d’applications de bureau Windows 8 ou d’applications Windows Server 2012, vous devez utiliser la méthode d’instrumentation. Vous ne pouvez pas collecter de données d’interaction de couche pour les applications UWP. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Vous pouvez inclure des données d’interaction de couche dans toutes les méthodes de profilage sur les autres versions prises en charge de Windows.

**Assistant Performance**

En raison d’un bogue dans l’Assistant Performance, vous devez ajouter l’option de collecte de données d’interaction de couche à une exécution du profilage à partir de l’Explorateur de performances. Vous devez aussi ajouter le projet, l’exécutable ou le site web au nœud cible de l’Explorateur de performances.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Pour ajouter des données d’interaction de couche à une exécution de profilage à l’aide des pages de propriétés de session de performance

1. Dans l’Explorateur de performances, choisissez **Propriétés** dans le menu contextuel.

2. Dans la page **Interactions de couche**, cochez la case **Activer le profilage d’interaction de couche**.

3. Dans l’Explorateur de performances, sélectionnez le nœud **Cibles**, puis spécifiez le projet, le fichier exécutable ou le site web que vous voulez profiler.

## <a name="see-also"></a>Voir aussi

[Interactions de couche, vue](../profiling/tier-interactions-view.md)