---
title: Vue Fonctions - Données d’échantillonnage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d478c00ef95644cd484c418dec92318dd1f5611
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304159"
---
# <a name="functions-view---sampling-data"></a>Vue Fonctions - Données d’échantillonnage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vue de rapport Fonctions de la méthode de profilage par échantillonnage répertorie les fonctions échantillonnées pendant l’exécution du profilage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Colonne|Description|  
|------------|-----------------|  
|**ID du processus**|ID du processus (PID) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
|**Fichier source**|Fichier source contenant la définition pour cette fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Échantillons inclusifs**|Nombre total d’échantillons collectés lorsque cette fonction était en cours d’exécution ; autrement dit, le nombre d’échantillons collectés lorsque cette fonction se trouvait sur la pile des appels. Ce nombre comprend les échantillons collectés lorsque les fonctions appelées par cette fonction étaient en cours d’exécution.|  
|**% des échantillons inclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons inclusifs de cette fonction.|  
|**Échantillons exclusifs**|Nombre total d’échantillons collectés lorsque le code du corps de cette fonction était exécuté ; autrement dit, lorsque cette fonction se trouvait en haut de la pile des appels. Ce nombre n’inclut pas les échantillons collectés dans les fonctions appelées par cette fonction.|  
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons de l’exécution du profilage qui étaient des échantillons exclusifs de cette fonction.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour personnaliser les colonnes de la vue Rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Vue Fonctions - Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vue Fonctions - Échantillonnage](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Mode Fonctions](../profiling/functions-view-instrumentation-data.md)



