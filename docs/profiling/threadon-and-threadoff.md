---
title: "ThreadOn et ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ThreadOn et ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les sous\-commandes **ThreadOff** et **ThreadOn** de VSPerfCmd.exe sont uniquement disponibles dans les sessions de profilage en ligne de commande qui utilisent la méthode d'instrumentation.  **ThreadOff** et **ThreadOn** suspendent et continuent le profilage du thread spécifié.  **ThreadOff** permet d'arrêter le profilage du thread et **ThreadOn** de le commencer.  
  
 Dans la plupart des cas, vous spécifiez **ThreadOn** ou **ThreadOff** comme une seule option dans une ligne de commande VSPerfCmd.exe, mais elles peuvent également être combinées avec les sous\-commandes **GlobalOn**, **GlobalOff**, **ProcessOn** et **ProcessOff**.  
  
 Les sous\-commandes **ThreadOff** et **ThreadOn** interagissent avec les sous\-commandes **GlobalOff** et **GlobalOn** qui contrôlent la collecte de données pour tous les processus d'une session de profilage en ligne de commande, et les sous\-commandes **ProcessOff** et **ProcessOn** qui contrôlent la collecte de données pour un processus spécifié.  
  
 Les sous\-commandes **ThreadOff** et **ThreadOn** affectent également la valeur Nombre de Start\/Stop du thread qui est manipulé par les fonctions de l'API du profileur.  
  
-   **ThreadOff** affecte immédiatement la valeur 0 au nombre Start\/Stop global et suspend ainsi le profilage.  
  
-   **ThreadOn** affecte immédiatement la valeur 1 au nombre Start\/Stop global et reprend ainsi le profilage.  
  
 Pour plus d’informations, consultez [API des outils de profilage](../profiling/profiling-tools-apis.md).  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### Paramètres  
 `TID`  
 Identificateur entier du thread à démarrer ou à arrêter.  
  
## Options valides  
 Les options **ThreadOn** et **ThreadOff** peuvent être spécifiées sur les lignes de commande qui contiennent également les sous\-commandes suivantes.  
  
 **Start:** `Method`  
 Initialise la session de profilage en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Arrête ou commence le profilage de tous les processus dans une session de profilage en ligne de commande.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Arrête ou commence le profilage pour le processus spécifié.  
  
## Exemple  
 Dans cet exemple, la sous\-commande **ThreadOff** est utilisée pour cesser de collecter les données de profilage afin que les seules données de démarrage de l'application soient collectées.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)