---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **WinCounter** spécifie un compteur de performance d'application ou Windows permettant de collecter des données à intervalles définis pendant l'exécution du profilage.  Les compteurs de performance d'application et Windows sont répertoriés sous la forme de marques dans le fichier de données de profilage.  Vous pouvez spécifier plusieurs compteurs de performance pour effectuer des collectes dans des options distinctes.  
  
 Par défaut, les compteurs sont collectés toutes les 500 millisecondes.  Utilisez l'option **AutoMark** pour spécifier un intervalle de collecte différent.  
  
 Une seule option **AutoMark** est utilisée.  Si plusieurs options **AutoMark** sont spécifiées, la dernière est utilisée.  
  
 L'option **WinCounter** ne peut être utilisée qu'avec l'option **Start**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### Paramètres  
 `Path`  
 Compteur de performance Windows au format de chemin d'accès du compteur PDH.  
  
## Options requises  
 L'option **WinCounter** ne peut être utilisée qu'avec l'option **Start**.  
  
 **Start:** `Method`  
 L'option **Start** initialise le profileur afin qu'il utilise la méthode de profilage spécifiée.  
  
## Options exclusives  
 L'option **AutoMark** ne peut être utilisée qu'avec l'option **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Spécifie le nombre de millisecondes entre les collectes de données du compteur de performance Windows.  
  
## Exemple  
 Dans l'exemple suivant, deux compteurs de performance Windows doivent être collectés à un intervalle de 1 000 millisecondes.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)