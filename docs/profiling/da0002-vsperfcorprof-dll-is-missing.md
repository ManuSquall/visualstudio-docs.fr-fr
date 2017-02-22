---
title: "DA0002&#160;: VSPerfCorProf.dll manquant | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002&#160;: VSPerfCorProf.dll manquant
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0002|  
|Catégorie|Utilisation des outils de profilage|  
|Méthodes de profilage|Profilage à l'aide des outils de ligne de commande VSPerfASPNETCmd et VSPerfCmd|  
|Message|Il semble que le fichier ait été collecté sans une configuration adéquate des variables d'environnement avec VSPerfCLREnv.cmd.  Les symboles pour des fichiers binaires managés peuvent ne pas être résolus.|  
|Type de règle|Information|  
  
## Cause  
 Le profileur n'a pas trouvé VSPerfCorProf.dll lors de l'exécution du profilage.  Cet avertissement se produit lorsque les outils en ligne de commande pour la collection de données du profileur sont utilisés sans l'outil VSPerfCLREnv.cmd pour initialiser les variables d'environnement nécessaires.  L'avertissement peut également se déclencher si un autre générateur de profils s'exécute lorsque les outils de profilage démarrent.  
  
## Description de la règle  
 Des variables d'environnement spécifiques doivent être définies avant une exécution du profilage afin que le profileur soit en mesure de résoudre les symboles dans les binaires .NET Framework.  Cet avertissement suggère que l'outil VSPerfCLREnv.cmd n'a pas été exécuté avant la collecte des données de profilage.  Les symboles pour les binaires managés ne peuvent pas être résolus.  Pour plus d'informations sur l'utilisation des Outils de profilage à partir de la ligne de commande, consultez [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## Comment corriger les violations  
 Lorsque vous profilez des applications managées à l'aide des outils en ligne de commande dans les Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], exécutez l'outil en ligne de commande [VSPerfCLREnv](../profiling/vsperfclrenv.md) avant de commencer à collecter des données.