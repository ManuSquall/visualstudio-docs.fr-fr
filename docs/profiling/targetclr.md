---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **TargetCLR** spécifie la version du Common Language Runtime \(CLR\) à profiler lorsque plusieurs versions du CLR sont chargées dans une application.  
  
 Par défaut, les outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ciblent la première version du CLR chargée par l'application.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### Paramètres  
 `ClrVersion`  
 Numéro de version du CLR.  Utilisez le format de version **vN.N.NNNNN**.  
  
## Options requises  
 L'option **TargetCLR** peut uniquement être utilisée avec les options **Launch** ou **Attach**.  
  
 **Launch:** `AppName`  
 Démarre l'application spécifiée et commence le profilage.  
  
 **Attach:** `PID`  
 Commence à profiler le processus spécifié.  
  
## Exemple  
 Dans cet exemple, l'option TargetCLR est utilisée pour s'assurer que le CLR version 4.0.11003 est profilé.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```