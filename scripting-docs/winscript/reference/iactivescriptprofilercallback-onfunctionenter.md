---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
Informe l'objet de profileur que le moteur de script est sur le point d'exécution d'un appel de fonction qui n'est pas un appel dans le modèle DOM \(DOM\).  
  
## Syntaxe  
  
```  
HRESULT OnFunctionEnter(  
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
 Pour les appels DOM, le moteur de script appelle [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) au lieu d' `IActiveScriptProfilerCallback::OnFunctionEnter`.  Cela est dû à le nombre de seules méthodes et propriétés dans le modèle DOM.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md)