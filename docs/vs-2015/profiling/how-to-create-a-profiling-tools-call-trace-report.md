---
title: Guide pratique pour créer un rapport de suivi des appels des Outils de profilage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547990"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Comment : créer un rapport de suivi d'appels des outils de profilage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le *rapport de suivi des appels* des Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] liste les informations chronologiques de chaque point d’entrée et de sortie des fonctions de votre application, et de chaque appel effectué par votre fonction à d’autres fonctions. Les rapports de suivi des appels sont disponibles pour les données de profilage seulement si elles ont été collectées avec la méthode d’instrumentation.  
  
> [!NOTE]
> Vous ne pouvez pas afficher des rapports de suivi des appels dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous devez utiliser l’outil en ligne de commande **VSPerfReport** pour générer un fichier .csv (valeurs séparées par des virgules) ou .xml. Pour plus d’informations sur cet outil, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Pour créer un rapport de suivi des appels  
  
1. Ouvrez une fenêtre **Invite de commandes**.  
  
2. Saisissez ensuite la commande suivante dans l’invite de commandes :  
  
     *chemin_outils* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |élément Command|Description|
    |-|-|  
    |*chemin_outils*|Chemin des outils en ligne de commande des Outils de profilage. Pour plus d’informations, consultez [Spécification du chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*fichier_VSP*|Fichier des données de profilage (.vsp ou .vsps). Les chemins complets et partiels sont acceptés.|  
    |Xml|Génère un rapport au format XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : collecter des données Suivi d’v nements pour Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API des outils de profilage](../profiling/profiling-tools-apis.md)
