---
title: Collecte de données d’interaction de couche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcdab1fcb776a729d00a143dfc318053b74c5cf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831500"
---
# <a name="collect-tier-interaction-data"></a>Collecter les données d’interaction de couche

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