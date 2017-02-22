---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option VSPerfCmd.exe **CrossSession** permet au profileur de collecter des données à partir de n'importe quelle session de console.  L'option **CrossSession** doit être utilisée avec l'option **Start**.  
  
 Vous pouvez utiliser l'abréviation **CS** en remplacement de **CrossSession**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### Paramètres  
 Aucun  
  
## Options valides  
 Pour permettre le profilage dans une autre session, l'option **CrossSession** doit être spécifiée avec l'option **Start**.  **CrossSession** doit également être spécifié dans les commandes **VSPerfCmd Attach** et **Detach** suivantes.  
  
 **Start:** `Method`  
 L'option **Start** initialise le profileur afin qu'il utilise la méthode de profilage spécifiée.  
  
 **Attach:** *PID*\[**,***PID*\]  
 Commence le profilage des processus spécifiés.  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 Arrête le profilage des processus spécifiés.  
  
## Exemple  
 Dans cet exemple, l'option **CrossSession** est utilisée pour attacher à une application démarrée dans une autre session de console.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)