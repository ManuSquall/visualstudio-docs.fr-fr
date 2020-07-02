---
title: Canaux (vue Threads) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df93a87285bdf1172e75b63ed956c1aa978fc71e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545533"
---
# <a name="channels-threads-view"></a>Canaux (vue Threads)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le visualiseur concurrentiel montre quatre types de canaux : les canaux de threads, les canaux de disques, les canaux de marqueurs et les canaux GPU.  
  
## <a name="thread-channels"></a>Canaux de threads  
 Un canal de thread affiche l’état d’un seul thread, à l’aide d’un système de couleurs. Lorsque vous pointez sur le nom du canal, la fonction de démarrage du thread en question s’affiche. Le visualiseur concurrentiel détecte plusieurs types de threads. Les types les plus courants sont présentés dans le tableau suivant.  
  
|Thread|Description|  
|-|-|  
|Thread principal|Thread qui a démarré l’application.|  
|Thread de travail|Thread qui a été créé par le thread principal de l’application.|  
|Thread de travail CLR|Thread de travail qui a été créé par le common language runtime (CLR).|  
|Assistance du débogueur|Thread de travail qui a été créé par le débogueur Visual Studio.|  
|Thread ConcRT|Thread qui a été créé par le runtime d’accès concurrentiel Microsoft.|  
|Thread GDI|Thread qui a été créé par GDIPlus.|  
|Thread OLE/RPC|Thread qui a été créé en tant que thread de travail RPC.|  
|Thread RPC|Thread qui a été créé en tant que thread RPC.|  
|Thread Winsock|Thread qui a été créé en tant que thread Winsock.|  
|Pool de threads|Thread qui a été créé par le pool de threads CLR.|  
  
## <a name="disk-channels"></a>Canaux de disques  
 Les canaux de disques correspondent aux lecteurs physiques de l’ordinateur. Chaque lecteur physique du système dispose de canaux distincts pour les opérations de lecture et d’écriture. Chaque lecteur dispose donc de deux canaux. Les numéros des disques correspondent aux noms des dispositifs de noyau. Un canal de disque s’affiche uniquement si le disque a connu une activité.  
  
## <a name="marker-channels"></a>Canaux de marqueurs  
 Les canaux de marqueurs correspondent aux événements générés par l’application et les bibliothèques qu’elle utilise. Par exemple, la bibliothèque parallèle de tâches, la bibliothèque de modèles parallèles et C++ AMP génèrent des événements qui s’affichent en tant que marqueurs. Chaque canal de marqueur est associé à un ID de thread, qui s’affiche à côté de la description du canal. L’ID identifie le thread qui a généré l’événement. La description du canal comprend le nom du fournisseur de suivi d’événements pour Windows (ETW) qui a généré les événements. Si le canal affiche les événements du [kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md), le nom de la série s’affiche également.  
  
## <a name="gpu-channels"></a>Canaux GPU  
 Les canaux GPU affichent des informations concernant l’activité DirectX 11 sur le système.  Chaque moteur DirectX qui est associé à la carte graphique dispose d’un canal distinct.  Chaque segment correspond à la durée de traitement d’un paquet DMA.  
  
## <a name="see-also"></a>Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)
