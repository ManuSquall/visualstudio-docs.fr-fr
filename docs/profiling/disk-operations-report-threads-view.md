---
title: "Rapport Opérations sur le disque (Vue Threads) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.report.diskoperations
helpviewer_keywords: Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7fcef6ffd829ea999c1ed8d62d34083f5adab46
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="disk-operations-report-threads-view"></a>Rapport Opérations sur le disque (Vue Threads)
Le rapport Opérations sur le disque affiche les opérations d’E/S de disque effectuées dans les canaux de disques.  
  
 Les informations suivantes sont signalées pour chaque accès au disque effectué pour le compte du processus en cours de profilage dans la fenêtre de temps actuellement visible :  
  
-   Le nom et le PID du processus qui a accédé au disque  
  
-   L’ID du thread qui a accédé au disque  
  
-   Le nom du fichier ayant fait l’objet d’un accès  
  
-   Le nombre de lectures par fichier  
  
-   Le nombre d’octets lus  
  
-   La latence de lecture, en millisecondes  
  
-   Le nombre d’écritures  
  
-   Le nombre d’octets écrits  
  
-   La latence d’écriture, en millisecondes  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)