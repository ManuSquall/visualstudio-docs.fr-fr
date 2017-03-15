---
title: "Comment&#160;: filtrer des rapports &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Comment&#160;: filtrer des rapports &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En utilisant des options pour la commande **VSPerfReport**  vous pouvez filtrer des rapports sur un segment de temps spécifique du fichier de données de profilage ou restreindre les données à un ou plusieurs processus ou threads.  Pour plus d'informations sur cette commande, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
|Options|Description|  
|-------------|-----------------|  
|**StartTime:**\[*Valeur*\]|Affiche uniquement les données collectées après la valeur \(en millisecondes\).|  
|**EndTime:**\[*Valeur*\]|Affiche uniquement les données collectées avant la valeur \(en millisecondes\).|  
|**FilterFile:** `VSPFFile`|Spécifie l'emplacement d'un fichier filtre qui a été généré depuis la fenêtre **Rapport de performances de Visual Studio**.|  
|**MsFilter:**\[*StartTime,Duration*\]|Affiche uniquement les données de `StartTime` jusqu'à la fin de la durée \(`Duration`\) en millisecondes.|  
|**Process:**\[*Pid*\]|Affiche uniquement les données du processus spécifié.|  
|**Thread:**\[*ThreadID*\]|Affiche uniquement les données du thread spécifié.|  
|**Thread:**\[*ThreadID,ProcessID*\]|Affiche uniquement les données du thread qui est associé au processus spécifié.|