---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **QueryCounters** répertorie les compteurs de performance UC \(matériel\) qui sont disponibles sur l'ordinateur.  
  
 **QueryCounters** doit être la seule option spécifiée sur la ligne de commande.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### Paramètres  
 Aucun  
  
## Notes  
 Lorsque vous utilisez la méthode d'instrumentation, le profileur peut collecter les valeurs d'un ou plusieurs compteurs de performance UC à chaque événement de collecte de données.  Lorsque vous utilisez la méthode de profilage de l'échantillonnage, vous pouvez spécifier un événement de compteur et le nombre d'occurrences d'événements à utiliser comme intervalle d'échantillonnage.  
  
 Différents processeurs exposent des compteurs de performance UC différents.  Le profileur définit un ensemble de compteurs génériques qui peuvent être utilisés sur presque tous les processeurs.  L'option **QueryCounters** répertorie à la fois les noms des compteurs génériques et les noms des compteurs qui sont spécifiques au processeur.  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)