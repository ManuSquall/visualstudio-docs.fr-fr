---
title: "Vue Durée de vie des objets | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d8fa19da70b55e4a519153898a800bb259983c39
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="object-lifetime-view"></a>Mode Durée de vie de l'objet
La vue Durée de vie des objets est disponible quand l’option **Collecter aussi les informations de durée de vie des objets .NET** est activée dans les pages de propriétés de la session de performance.  
  
 Le récupérateur de mémoire du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] gère l’allocation et la libération de mémoire pour votre application. Pour optimiser les performances du garbage collector, le tas managé est divisé en trois générations : 0, 1 et 2. Le récupérateur de mémoire du runtime stocke les nouveaux objets dans la génération 0. Les objets qui survivent aux collectes sont promus et stockés dans les générations 1 et 2.  
  
 Le récupérateur de mémoire récupère de la mémoire en désallouant une génération entière d’objets. Pour les objets créés par l’application profilée, la vue Durée de vie des objets montre le nombre et la taille des objets, ainsi que la génération auprès de laquelle ils sont récupérés.  
  
## <a name="general"></a>Général  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nom de classe**|Nom de classe du type alloué.|  
|**ID du processus**|ID de processus de l’exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom du module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d’accès du module qui contient la fonction.|  
  
## <a name="instance-data"></a>Données d’instance  
 Les données d’instance indiquent le nombre d’objets du type qui ont été créés lors de l’exécution du profilage, et la génération dans laquelle les objets ont été désalloués par le récupérateur de mémoire.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Instances**|Nombre d’allocations d’objets de ce type.|  
|**% du nombre total d’instances**|Pourcentage du nombre total d’allocations qui ont été effectuées lors de l’exécution du profilage.|  
|**Instances de la génération 0 collectées**|Nombre d’instances du type qui ont été désallouées dans la génération 0 de l’algorithme de garbage collection.|  
|**Instances de la génération 1 collectées**|Nombre d’instances du type qui ont été désallouées dans la génération 1 de l’algorithme de garbage collection.|  
|**Instances de la génération 2 collectées**|Nombre d’instances du type qui ont été désallouées dans la génération 2 de l’algorithme de garbage collection.|  
|**Instances actives à la fin**|Nombre d’instances du type qui n’ont pas été désallouées jusqu’à la fin de l’exécution du profilage.|  
  
## <a name="size-byte-data"></a>Données de taille (octets)  
 Les données de taille (octets) indiquent la taille des objets du type qui ont été créés lors de l’exécution du profilage, et la quantité de mémoire qui a été récupérée dans chaque génération où les objets ont été désalloués.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Nombre total d’octets alloués**|Nombre total d’octets de toutes les instances du type.|  
|**% du nombre total d’octets**|Pourcentage du nombre total d’octets alloués dans l’exécution du profilage et qui ont été alloués pour les instances de ce type.|  
|**Octets de la génération 0 collectés**|Taille des instances du type qui ont été désallouées dans la génération 0 de l’algorithme de garbage collection.|  
|**Octets de la génération 1 collectés**|Taille des instances du type qui ont été désallouées dans la génération 1 de l’algorithme de garbage collection.|  
|**Octets de la génération 2 collectés**|Taille des instances du type qui ont été désallouées dans la génération 2 de l’algorithme de garbage collection.|  
  
## <a name="large-object-heap-data"></a>Taille du tas des objets volumineux  
 L’allocateur de mémoire .NET gère les objets très volumineux à un emplacement qui est distinct du tas géré standard. Les données du tas des objets volumineux indiquent le nombre et la taille des objets du type qui étaient gérés à cet emplacement.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Instances du tas des objets volumineux collectées**|Nombre d’instances de ce type qui ont été placées dans le tas des objets volumineux et qui ont été collectées lors de l’exécution du profilage.|  
|**Octets du tas des objets volumineux collectés**|Taille en octets des instances de ce type qui ont été placées dans le tas des objets volumineux et qui ont été collectées lors de l’exécution du profilage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)