---
title: "Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Shutdown
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Shutdown** attend la fin ou le détachement d'un processus en cours de profilage, puis désactive le profileur et ferme le fichier de données de profilage.  L'option **Shutdown** doit être la dernière commande d'une exécution de profilage.  
  
 Si aucun paramètre de délai d'expiration n'est spécifié, l'option **Shutdown** attendra indéfiniment.  Si un paramètre de délai d'expiration est spécifié, l'option est retournée après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données.  
  
 L'option **Shutdown** doit être la seule option spécifiée sur la ligne de commande.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### Paramètres  
 `Timeout`  
 -   \(Facultatif\) Si une valeur est précisée, l'option est retournée après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données de profilage.  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)