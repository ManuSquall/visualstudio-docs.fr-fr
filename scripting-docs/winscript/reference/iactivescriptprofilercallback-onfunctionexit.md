---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
Informe l'objet de profileur que le moteur de script terminée exécution d'un appel de fonction qui n'est pas un appel dans le modèle DOM \(DOM\).  
  
## Syntaxe  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### Paramètres  
 `scriptId`  
 \[in\]  ID unique du script que la fonction fait partie de.  Cet ID est assigné par le moteur de script.  
  
 `functionId`  
 \[in\]  ID unique de la fonction.  Cet ID est assigné par le moteur de script.  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## Notes  
 Pour les appels DOM, le moteur de script appelle [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) au lieu d' `IActiveScriptProfilerCallback::OnFunctionExit`.  Cela est dû à le nombre de seules méthodes et propriétés dans le modèle DOM.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md)