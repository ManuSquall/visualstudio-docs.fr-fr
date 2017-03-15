---
title: "Console | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Console** de VSPerfCmd.exe démarre l'application spécifiée dans une nouvelle fenêtre d'invite de commandes.  L'option **Console** ne peut être utilisée qu'avec l'option **Launch** VSPerfCmd.  Si l'application n'est pas une application en ligne de commande, **Console** n'a aucun effet.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### Paramètres  
 Aucun  
  
## Options requises  
 **Console** peut être spécifié uniquement sur une ligne de commande qui contient également l'option **Launch**.  
  
 **Launch:** `AppName`  
 Démarre le profileur et l'application spécifiés par `AppName`.  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)