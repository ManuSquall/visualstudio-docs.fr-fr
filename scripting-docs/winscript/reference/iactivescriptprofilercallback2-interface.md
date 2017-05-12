---
title: "IActiveScriptProfilerCallback2, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2 (interface)"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback2, interface
Fournit des méthodes utilisées par le moteur de script pour avertir un objet de profileur lorsque les événements de \(DOM\) de modèle DOM se produisent.  Cette interface est implémentée par l'objet de profileur.  
  
## Méthodes  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Informe l'objet de profileur que le moteur de script va exécuter un appel de fonction DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Informe l'objet de profileur que le moteur de script est terminé d'exécuter un appel de fonction DOM.|  
  
## Remarques  
 l'interface d' `IActiveScriptProfilerCallback2` d'abord libérée avec Internet Explorer 9.  
  
 La notification des appels de fonction qui ne sont pas des appels dans le modèle DOM est fournie par [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Pour ajouter la possibilité de démarrer et arrêter le profilage lorsqu'un script s'exécute, appelez les méthodes suivantes.  À l'aide de ces méthodes, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute lorsque vous démarrez ou arrêter le profilage.  
>   
>  -   Appelez [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) pour informer le profileur que vous avez commencé à profiler.  
> -   Appelez [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pour informer le profileur que vous cesserez bientôt de profilage.  
  
## Voir aussi  
 [Profilage de script actif, interfaces](../../winscript/reference/active-script-profiler-interfaces.md)