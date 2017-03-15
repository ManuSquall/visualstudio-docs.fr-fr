---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **AutoMark** spécifie le nombre de millisecondes entre deux collectes d'événements du compteur de performance logiciel Windows.  Les compteurs de performance Windows sont spécifiés dans l'option **WinCounter**.  
  
 Vous ne pouvez spécifier qu'une seule option **AutoMark** sur la ligne de commande.  Notez que l'intervalle d'échantillonnage **WinCounter** spécifié par **AutoMark** est indépendant de l'intervalle d'échantillonnage principal.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### Paramètres  
 `Milliseconds`  
 Spécifie le nombre de millisecondes entre deux collectes d'événements de compteur de performance Windows.  
  
## Options requises  
 **WinCounter:** `Path`  
 Spécifie le compteur de performance Windows à collecter.  Lorsque vous utilisez la méthode d'instrumentation, plusieurs compteurs Windows peuvent être spécifiés.  Lorsque vous utilisez la méthode d'échantillonnage, un seul compteur logiciel peut être spécifié.  L'option **WinCounter** doit être spécifiée sur une ligne de commande qui contient l'option **Start**.  
  
## Exemple  
 Dans cet exemple, un intervalle d'échantillonnage de 1000 millisecondes est défini pour deux compteurs de performance Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)