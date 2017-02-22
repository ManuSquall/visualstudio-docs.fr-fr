---
title: "Collecte des donn&#233;es sur l’interaction de couche &#224; l’aide de l’IDE de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.tierinteraction"
helpviewer_keywords: 
  - "Outils de profilage, profilage ADO.NET"
  - "profilage d’interaction de couche, méthode"
  - "outils de profilage, méthode d’interaction de couche"
  - "profilage des performances ADO.NET"
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Collecte des donn&#233;es sur l’interaction de couche &#224; l’aide de l’IDE de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le profilage des interactions entre les couches fournit des informations supplémentaires sur les temps d'exécution dans les fonctions des applications multicouches qui communiquent avec les bases de données via les services ADO.NET.  Les données sont collectées uniquement pour les appels de fonction synchrones.  
  
 **Éditions Visual Studio**  
  
 Les données de profilage d'interaction de couche peuvent être collectées à l'aide de Visual Studio Ultimate, Premium Visual Studio, ni Visual Studio Professional.  Toutefois, les données de profilage d'interaction de couche peuvent être affichées uniquement dans VS final et VS Premium.  
  
 **Windows 8 et Windows Server 2012**  
  
 Pour collecter des données sur l'interaction entre les couches sur les applications Windows 8 e bureau et Windows Server de 2012, vous devez utiliser la méthode d'instrumentation.  Vous ne pouvez pas collecter des données sur l'interaction entre les couches pour les applications du Windows Store.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  Vous pouvez inclure des données sur l'interaction entre les couches dans toutes les méthodes de profilage sur l'autre version de Windows prise en charge.  
  
 **Performance \(Assistant\)**  
  
 En raison d'un bogue dans l'Assistant Performance, vous devez ajouter l'option de collection de données sur l'interaction entre les couches à une exécution du profilage Explorateur de performances.  Vous devez également ajouter le projet, le fichier exécutable, ou le site Web au nœud cible Explorateur de performances.  
  
### Pour ajouter des données sur l'interaction entre les couches à une exécution du profilage à l'aide des pages de propriétés de la session de performance  
  
1.  Dans l'Explorateur de performances, choisissez **Propriétés** dans le menu contextuel.  
  
2.  Sélectionner la page **Interaction de Couches** activez la case à cocher **Activer le profilage d'interaction de couche**.  
  
3.  Dans l'Explorateur de performances, sélectionnez le nœud **Cibles**, puis spécifiez le projet, le fichier exécutable, ou le site Web que vous souhaitez profiler.  
  
## Voir aussi  
 [Interactions de couche, vue](../profiling/tier-interactions-view.md)