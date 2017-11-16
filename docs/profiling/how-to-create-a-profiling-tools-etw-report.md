---
title: "Guide pratique pour créer un rapport Suivi d’événements pour Windows (ETW) des outils de profilage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8cd2bd1765da67ee86b1cfb3acf5867fa215823
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Guide pratique pour créer un rapport Suivi d’événements pour Windows (ETW) des outils de profilage
Le rapport Suivi d’événements pour Windows (ETW) répertorie les événements de suivi d’événements pour Windows enregistrés dans une session de performances des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les données de suivi d’événements pour Windows sont collectées dans un fichier binaire (.etl). Pour plus d’informations sur ce rapport, consultez [Rapport Suivi d’événements pour Windows](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Vous ne pouvez pas afficher les rapports de suivi d’événements pour Windows dans l’interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Pour plus d’informations sur la collecte des données de suivi d’événements pour Windows à l’aide de l’interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Pour plus d’informations sur la collecte des données de suivi d’événements pour Windows à partir d’une invite de commandes, consultez [VSPerfCmd](../profiling/vsperfcmd.md) et [Événements](../profiling/events-vsperfcmd.md).  
  
 Vous générez le rapport de suivi d’événements pour Windows en utilisant la commande **VSReport/summary:etw**. Le fichier .etl qui contient les données de suivi d’événements pour Windows doit être dans le même répertoire que le fichier des données de profilage (.vsp ou .vsps). Par défaut, le rapport est généré sous la forme d’un fichier de valeurs séparées par des virgules (.csv). Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Pour générer un rapport Suivi d’événements pour Windows  
  
-   Dans une fenêtre **Invite de commandes**, exécutez la commande suivante :  
  
     *chemin_outils* **VSPerfReport** *fichier_VSP*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*chemin_outils*|Chemin de l’utilitaire Outils de profilage. Pour plus d’informations, consultez [Spécification du chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*fichier_VSP*|Fichier des données de profilage (.vsp ou .vsps). Les chemins complets et partiels sont acceptés.|  
    |Xml|Génère un rapport au format XML.|