---
title: "ProcessOn et ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ProcessOn et ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les sous\-commandes **ProcessOff** et **ProcessOn** de VSPerfCmd.exe suspendent et reprennent le profilage du processus spécifié dans une session de profilage en ligne de commande.  **ProcessOff** cesse de profiler le processus et **ProcessOn** commence à profiler le processus.  
  
 Dans la plupart des cas, vous spécifiez **ProcessOn** ou **ProcessOff** comme seule option dans une ligne de commande VSPerfCmd.exe, mais elles peuvent également être combinés avec les sous\-commandes **GlobalOn**, **GlobalOff**, **ThreadOn** et **ThreadOff**.  
  
 Les sous\-commandes **ProcessOff** et **ProcessOn** interagissent avec les sous\-commandes **GlobalOff** et **GlobalOn** qui contrôlent la collecte de données pour tous les processus d'une session de profilage en ligne de commande, et les sous\-commandes **ThreadOff** et **ThreadOn** qui contrôlent la collecte de données pour un thread spécifié.  
  
 Les sous\-commandes **ProcessOff** et **ProcessOn** affectent également la valeur Nombre de Start\/Stop du processus qui est manipulé par les fonctions de l'API du profileur.  
  
-   **ProcessOff** affecte immédiatement la valeur 0 à Nombre de Start\/Stop du processus et suspend ainsi le profilage.  
  
-   **ProcessOn** affecte immédiatement la valeur 1 à Nombre de Start\/Stop du processus et reprend ainsi le profilage.  
  
 Pour plus d’informations, consultez [API des outils de profilage](../profiling/profiling-tools-apis.md).  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### Paramètres  
 `PID`  
 Identificateur entier du processus à démarrer ou arrêter.  Les ID de processus sont répertoriés sous l'onglet Processus du Gestionnaire des tâches Windows.  
  
## Sous\-commandes obligatoires  
 Aucun  
  
## Sous\-commandes valides  
 Les options **ProcessOn** et **ProcessOff** peuvent être spécifiées sur les lignes de commande qui contiennent également les sous\-commandes suivantes.  
  
 **Start:** `Method`  
 Initialise la session de profilage en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **Launch:** `AppName`  
 Démarre l'application spécifiée et commence le profilage avec la méthode d'échantillonnage.  
  
 **Attach:** `PID`  
 Commence le profilage du processus spécifié.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Arrête ou commence le profilage de tous les processus dans une session de profilage en ligne de commande.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Arrête ou démarre le profilage du thread spécifié \(méthode d'instrumentation uniquement\).  
  
## Exemple  
 Dans cet exemple, la sous\-commande **ProcessOff** est utilisée pour collecter les données de profilage pour le démarrage de l'application.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)