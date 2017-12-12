---
title: "Suivi des événements pour Windows (ETW), rapport | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ae3b43f300ce410f58dd3fc4d849b2fe1bb3c38
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="event-tracing-for-windows-etw-report"></a>Suivi des événements pour Windows (ETW), rapport
Le rapport Suivi des événements pour Windows (ETW) liste les événements ETW enregistrés dans une session de performances des Outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les données de suivi des événements pour Windows sont collectées dans un fichier binaire (.etl).  
  
> [!NOTE]
>  Vous ne pouvez pas afficher les rapports de suivi des événements pour Windows dans l’interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Pour plus d’informations sur la collecte des données de suivi des événements pour Windows en utilisant les Outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Guide pratique pour collecter les données de suivi des événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
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