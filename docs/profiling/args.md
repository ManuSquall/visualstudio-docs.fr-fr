---
title: "Args | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Args
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Args** de VSPerfCmd.exe spécifie une liste des arguments passés à l'application cible de la sous\-commande **Launch**.  
  
 **Args** ne peut être utilisé que lorsque **Launch** est également spécifié sur la ligne de commande.  **Args** est facultatif lorsque **Launch** est spécifié.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### Paramètres  
 `Arguments`  
 Liste des arguments pour l'application cible de la commande **Launch**.  
  
## Options requises  
 **Launch:** `AppName`  
 Démarre l'application spécifiée et commence le profilage avec la méthode d'échantillonnage.  
  
## Exemple  
 L'exemple suivant utilise l'option **Args** pour passer des arguments à TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)