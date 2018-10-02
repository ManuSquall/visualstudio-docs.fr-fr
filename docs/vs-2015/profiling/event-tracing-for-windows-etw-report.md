---
title: Suivi des événements pour Windows (ETW), rapport | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49ea37f6830c7e4fdf8c8d94b0f323c6337329c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508489"
---
# <a name="event-tracing-for-windows-etw-report"></a>Suivi d'événements pour Windows (ETW), rapport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [rapport de suivi d’événements pour Windows (ETW)](https://docs.microsoft.com/visualstudio/profiling/event-tracing-for-windows-etw-report).  
  
Le rapport Suivi des événements pour Windows (ETW) liste les événements ETW enregistrés dans une session de performances des Outils de profilage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Les données de suivi d’événements pour Windows sont collectées dans un fichier binaire (.etl).  
  
> [!NOTE]
>  Vous ne pouvez pas afficher les rapports de suivi des événements pour Windows dans l’interface de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Pour plus d’informations sur la collecte des données de suivi des événements pour Windows en utilisant les Outils de profilage de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Guide pratique pour collecter les données de suivi des événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Pour plus d’informations sur la collecte des données de suivi des événements pour Windows en utilisant les outils de ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), consultez [Événements](../profiling/events-vsperfcmd.md).  
  
-   Vous générez le rapport de suivi d’événements pour Windows en utilisant la commande **VSReport/Summary:ETW**. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
|Colonne|Description|  
|------------|-----------------|  
|**Horodatage**|Identifie quand l’événement s’est produit.|  
|**ID du processus**|Identifie le processus qui a généré l’événement.|  
|**ID de thread**|Identifie le thread qui a généré l’événement.|  
|**Description**|Identifie le fournisseur d’événements.|  
|**Type**|Identifie le type d’événement.|  
|**Propriétés**|Propriétés de l’événement. Chaque événement est une paire nom-valeur avec la virgule comme séparateur, qui est placée entre des crochets.|



