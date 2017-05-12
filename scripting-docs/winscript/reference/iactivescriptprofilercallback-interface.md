---
title: "IActiveScriptProfilerCallback, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptProfilerCallback, interface
Fournit des méthodes utilisées par le moteur de script pour avertir un objet de profileur lorsque des événements se produisent.  Cette interface est implémentée par l'objet de profileur.  
  
## Méthodes  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Appelé pour initialiser l'objet de profileur chaque fois que le profilage est démarré dans un moteur de script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Appelé pour libérer et libérer l'objet de profileur chaque fois que le profilage est arrêté sur un moteur de script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Informe l'objet de profileur que le moteur de script est compilé le script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Informe l'objet de profileur que le moteur de script a rencontré une fonction lors de la compilation d'un script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Informe l'objet de profileur que le moteur de script est sur le point d'exécution d'un appel de fonction qui n'est pas un appel dans le modèle DOM \(DOM\).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Informe l'objet de profileur que le moteur de script terminée exécution d'un appel de fonction qui n'est pas un appel dans le modèle DOM.|  
  
## Remarques  
 La notification des appels de fonction dans le document object model \(DOM\) est fournie par [IActiveScriptProfilerCallback2, interface](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Pour ajouter la possibilité de démarrer et arrêter le profilage lorsqu'un script s'exécute, appelez les méthodes suivantes.  À l'aide de ces méthodes, vous pouvez obtenir la pile des appels complète si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute lorsque vous démarrez ou arrêter le profilage.  
>   
>  -   Appelez [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) pour informer le profileur que vous avez commencé à profiler.  
> -   Appelez [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) pour informer le profileur que vous cesserez bientôt de profilage.  
  
## Voir aussi  
 [Profilage de script actif, interfaces](../../winscript/reference/active-script-profiler-interfaces.md)