---
title: Rapport Opérations sur le disque (Vue Threads) | Microsoft Docs
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
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f121b8939ff55c9274cd04560ae7d507e22fde5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245152"
---
# <a name="disk-operations-report-threads-view"></a>Rapport Opérations sur le disque (Vue Threads)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [vue Threads](../profiling/threads-view-parallel-performance.md)



