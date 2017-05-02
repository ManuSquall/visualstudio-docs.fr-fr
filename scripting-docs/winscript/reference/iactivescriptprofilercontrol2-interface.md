---
title: "IActiveScriptProfilerControl2, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2 (interface)"
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2, interface
Fournit des méthodes qui ajoutent la capacité de démarrer ou arrêter le profilage lorsqu'un script s'exécute.  
  
## Méthodes  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Informe le profileur que vous avez commencé à profiler sur tous les moteurs de script applicables.  Cela vous permet d'obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute lorsque vous commencez à profiler.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Informe le profileur que vous souhaitez arrêter le profilage sur tous les moteurs de script applicables.  Cela vous permet d'obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute lorsque vous arrêtez de profilage.|  
  
## Voir aussi  
 [IActiveScriptProfilerControl, interface](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Profilage de script actif, interfaces](../../winscript/reference/active-script-profiler-interfaces.md)