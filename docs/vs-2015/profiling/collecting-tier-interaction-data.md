---
title: Collecte de données d’interaction de couche | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e2d46992b48b987966bac7d7dc68787f4016c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761187"
---
# <a name="collecting-tier-interaction-data"></a>Collecte de données d’interaction de couche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le profilage d’interaction de couche fournit des informations supplémentaires sur les temps d’exécution des fonctions d’applications multicouches qui communiquent avec des bases de données via les services ADO.NET. Les données sont collectées uniquement pour les appels de fonctions synchrones.  
  
 **Éditions Visual Studio**  
  
 Les données de profilage d’interaction de couche peuvent être collectées à l’aide de Visual Studio Ultimate, Visual Studio Premium ou Visual Studio Professional. Cependant, les données de profilage d’interaction de couche ne peuvent être affichées que dans Visual Studio Ultimate et Visual Studio Premium.  
  
 **Windows 8 et Windows Server 2012**  
  
 Pour collecter des données d’interaction de couche à partir d’applications de bureau Windows 8 ou d’applications Windows Server 2012, vous devez utiliser la méthode d’instrumentation. Vous ne pouvez pas collecter de données d’interaction de couche pour les applications du Windows Store. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Vous pouvez inclure des données d’interaction de couche dans toutes les méthodes de profilage sur les autres versions prises en charge de Windows.  
  
 **Assistant Performance**  
  
 En raison d’un bogue dans l’Assistant Performance, vous devez ajouter l’option de collecte de données d’interaction de couche à une exécution du profilage à partir de l’Explorateur de performances. Vous devez aussi ajouter le projet, l’exécutable ou le site web au nœud cible de l’Explorateur de performances.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Pour ajouter des données d’interaction de couche à une exécution de profilage à l’aide des pages de propriétés de session de performance  
  
1.  Dans l’Explorateur de performances, choisissez **Propriétés** dans le menu contextuel.  
  
2.  Dans la page **Interactions de couche**, cochez la case **Activer le profilage d’interaction de couche**.  
  
3.  Dans l’Explorateur de performances, sélectionnez le nœud **Cibles**, puis spécifiez le projet, le fichier exécutable ou le site web que vous voulez profiler.  
  
## <a name="see-also"></a>Voir aussi  
 [Interactions de couche, vue](../profiling/tier-interactions-view.md)



