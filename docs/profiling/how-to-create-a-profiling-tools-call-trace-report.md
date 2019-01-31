---
title: 'Procédure : Créer un rapport de suivi des appels des Outils de profilage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d38bc320e2c1604930c5f5767408876089e4119a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004858"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procédure : Créer un rapport de suivi d’appels des outils de profilage
Le *rapport de suivi des appels* des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] liste les informations chronologiques de chaque point d’entrée et de sortie des fonctions de votre application, et de chaque appel effectué par votre fonction à d’autres fonctions. Les rapports de suivi des appels sont disponibles pour les données de profilage seulement si elles ont été collectées avec la méthode d’instrumentation.  
  
> [!NOTE]
>  Vous ne pouvez pas afficher des rapports de suivi des appels dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous devez utiliser l’outil en ligne de commande **VSPerfReport** pour générer un fichier .*csv* (valeurs séparées par des virgules) ou .*xml*. Pour plus d’informations sur cet outil, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Pour créer un rapport de suivi des appels  
  
1.  Ouvrez une fenêtre **Invite de commandes**.  
  
2.  À l'invite de commandes, tapez la commande suivante :  
  
     *chemin_outils* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*chemin_outils*|Chemin des outils en ligne de commande des Outils de profilage. Pour plus d’informations, consultez [Spécifier le chemin d’accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*fichier_VSP*|Fichier des données de profilage (.*vsp* ou .*vsps*). Les chemins complets et partiels sont acceptés.|  
    |Xml|Génère un rapport au format XML.|  

  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API des outils de profilage](../profiling/profiling-tools-apis.md)
