---
title: "Mode Dur&#233;e de vie de l&#39;objet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.objectlifetime"
helpviewer_keywords: 
  - "durée de vie, objets"
  - "Durée de vie des objets (mode)"
  - "rapports de performances, mode Durée de vie des objets"
  - "rapports d'outils de profilage, mode Durée de vie"
  - "outils de profilage, mode Durée de vie"
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Mode Dur&#233;e de vie de l&#39;objet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Durée de vie de l'objet est disponible lorsque l'option **Collecter aussi les informations de durée de vie des objets .NET** est activée sur les pages de propriétés de la session de performance.  
  
 Le garbage collector \(également appelé ramasse\-miettes\) du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] gère l'allocation et la libération de mémoire dans votre application.  Pour optimiser les performances du garbage collector, le tas managé est divisé en trois générations : 0, 1 et 2.  Le garbage collector du runtime stocke les nouveaux objets dans la génération 0.  Les objets qui survivent aux collectes sont promus et stockés dans les générations 1 et 2.  
  
 Le garbage collector libère de la mémoire en libérant une génération entière d'objets.  Pour les objets créés par l'application profilée, le mode Durée de vie de l'objet affiche le nombre et la taille des objets, ainsi que la génération depuis laquelle ils sont libérés.  
  
## Général  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom de la classe**|Nom de la classe du type alloué.|  
|**ID de processus**|ID de processus de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
  
## Données d'instance  
 Les données d'instance indiquent le nombre d'objets du type créés dans l'exécution du profilage, et la génération dans laquelle les objets ont été libérés par le garbage collector.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Instances**|Nombre d'allocations d'objets de ce type.|  
|**% du nombre total d'instances**|Pourcentage du nombre total d'allocations effectuées dans l'exécution du profilage.|  
|**Instances de la génération 0 collectées**|Nombre d'instances du type libérées dans la génération 0 de l'algorithme de garbage collection.|  
|**Instances de la génération 1 collectées**|Nombre d'instances du type libérées dans la génération 1 de l'algorithme de garbage collection.|  
|**Instances de la génération 2 collectées**|Nombre d'instances du type libérées dans la génération 2 de l'algorithme de garbage collection.|  
|**Instances actives à la fin**|Nombre d'instances du type qui n'ont pas été libérées avant la fin de l'exécution du profilage.|  
  
## Données de taille \(en octets\)  
 Les données de taille \(en octets\) indiquent la taille des objets du type créés dans l'exécution du profilage, et la quantité de mémoire libérée dans chaque génération au cours de laquelle les objets ont été libérés.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nombre total d'octets alloué**|Nombre total d'octets alloués pour toutes les instances du type.|  
|**% du nombre total d'octets**|Pourcentage du nombre total d'octets alloués lors de l'exécution du profilage pour les instances de ce type.|  
|**Octets de la génération 0 collectés**|Taille des instances du type libérées dans la génération 0 de l'algorithme de garbage collection.|  
|**Octets de la génération 1 collectés**|Taille des instances du type libérées dans la génération 1 de l'algorithme de garbage collection.|  
|**Octets de la génération 2 collectés**|Taille des instances du type libérées dans la génération 2 de l'algorithme de garbage collection.|  
  
## Données du tas des objets volumineux  
 L'allocateur de mémoire .NET gère les objets très volumineux dans un emplacement distinct du tas managé standard.  Les données du tas des objets volumineux indiquent le nombre et la taille des objets du type gérés dans cet emplacement.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Instances collectées du tas des objets volumineux**|Nombre d'instances de ce type situées dans le tas des objets volumineux et collectées dans l'exécution du profilage.|  
|**Octets collectés du tas des objets volumineux**|Taille en octets des instances de ce type situées dans le tas des objets volumineux et collectées dans l'exécution du profilage.|  
  
## Voir aussi  
 [Vues de données de mémoire .NET](../profiling/dotnet-memory-data-views.md)