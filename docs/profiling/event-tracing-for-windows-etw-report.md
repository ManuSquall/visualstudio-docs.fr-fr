---
title: "Suivi d&#39;&#233;v&#233;nements pour Windows (ETW), rapport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilage ETW (report)"
  - "Traçage d'événements pour Windows (rapport de profilage)"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Suivi d&#39;&#233;v&#233;nements pour Windows (ETW), rapport
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le rapport du Suivi d'événements pour Windows \(ETW\) répertorie les événements ETW enregistrés dans une session de performance des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Les données ETW sont collectées dans un fichier binaire \(.etl\).  
  
> [!NOTE]
>  Vous ne pouvez pas afficher de rapports ETW dans l'interface [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Pour plus d'informations sur la façon de collecter ETW en utilisant les outils de profilage à partir de l'interface [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Comment : collecter les données de suivi d’événements pour Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md).  
  
-   Pour plus d'informations sur la collecte des données ETW en utilisant les outils en ligne de commande [VSPerfCmd](../profiling/vsperfcmd.md), consultez [Événements](../profiling/events-vsperfcmd.md).  
  
-   Vous générez le rapport ETW en utilisant la commande **VSReport\/Summary:ETW**.  Pour plus d'informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Horodateur**|Identifie quand l'événement s'est produit.|  
|**ID de processus**|Identifie le processus qui a généré l'événement.|  
|**ID de thread**|Identifie le thread qui a généré l'événement.|  
|**Description**|Identifie le fournisseur d'événements.|  
|**Type**|Identifie le type d'événements.|  
|**Propriétés**|Propriétés de l'événement.  Chaque événement est une paire nom\-valeur entre parenthèse séparée par une virgule.|