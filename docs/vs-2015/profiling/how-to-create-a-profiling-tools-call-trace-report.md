---
title: Guide pratique pour créer un rapport de suivi des appels des Outils de profilage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b3d54c0d9c053b8ea35b6f8000135b259f8323a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251899"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Comment : créer un rapport de suivi d'appels des outils de profilage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le *rapport de suivi des appels* des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] liste les informations chronologiques de chaque point d’entrée et de sortie des fonctions de votre application, et de chaque appel effectué par votre fonction à d’autres fonctions. Les rapports de suivi des appels sont disponibles pour les données de profilage seulement si elles ont été collectées avec la méthode d’instrumentation.  
  
> [!NOTE]
>  Vous ne pouvez pas afficher des rapports de suivi des appels dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous devez utiliser l’outil en ligne de commande **VSPerfReport** pour générer un fichier .csv (valeurs séparées par des virgules) ou .xml. Pour plus d’informations sur cet outil, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Pour créer un rapport de suivi des appels  
  
1.  Ouvrez une fenêtre **Invite de commandes**.  
  
2.  À l'invite de commandes, tapez la commande suivante :  
  
     *chemin_outils* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*chemin_outils*|Chemin des outils en ligne de commande des Outils de profilage. Pour plus d’informations, consultez [Spécification du chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*fichier_VSP*|Fichier des données de profilage (.vsp ou .vsps). Les chemins complets et partiels sont acceptés.|  
    |Xml|Génère un rapport au format XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API des outils de profilage](../profiling/profiling-tools-apis.md)



