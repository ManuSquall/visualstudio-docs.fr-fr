---
title: "Comment&#160;: cr&#233;er un rapport de suivi d&#39;appels des outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW (Visual Studio ALM), afficher des données"
  - "outils d'analyse des performances, afficher des données ETW"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: cr&#233;er un rapport de suivi d&#39;appels des outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le *rapport de suivi d'appels* des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] répertorie les informations de temporisation pour chaque point d'entrée et de sortie de vos fonctions d'application et chaque appel passé à d'autres fonctions par votre fonction.  Les rapports de suivi d'appel sont uniquement disponibles pour les données de profilage si elles ont été collectées avec la méthode d'instrumentation.  
  
> [!NOTE]
>  Vous ne pouvez pas afficher des rapports de suivi d'appel dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vous devez utiliser l'outil en ligne de commande **VSPerfReport** pour générer un fichier .csv ou Xml.  Pour plus d'informations sur cet outil, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
### Pour créer un rapport de suivi d'appel  
  
1.  Ouvrez une fenêtre **Invite de commandes**.  
  
2.  À l'invite de commandes, tapez la commande suivante :  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Chemin d'accès aux outils en ligne de commande des outils de profilage.  Pour plus d'informations, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Fichier de données de profilage \(.vsp ou .vsps\).  Les chemins d'accès complets et partiels sont acceptés.|  
    |Xml|Crée un rapport au format Xml.|  
  
## Voir aussi  
 [Comment : collecter les données de suivi d’événements pour Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [API des outils de profilage](../profiling/profiling-tools-apis.md)