---
title: "Output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Output
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Output** spécifie le nom du fichier de données de profilage pour la session de performance.  **Output** doit être utilisée avec l'option **Start**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Paramètres  
 `FileName`  
 Nom du fichier de données.  Les chemins d'accès complets et partiels sont acceptés.  Si aucun nom n'est spécifié, le fichier est créé dans le répertoire actif.  
  
## Options requises  
 L'option **Output** doit être utilisée avec l'option **Start**.  
  
 **Start:** `Method`  
 Spécifie le nom du fichier de sortie.  
  
## Exemple  
 Dans l'exemple suivant, le fichier de données de profilage est créé dans le répertoire actif.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)