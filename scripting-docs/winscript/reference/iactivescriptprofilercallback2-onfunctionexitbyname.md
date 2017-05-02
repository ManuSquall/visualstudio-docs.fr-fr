---
title: "IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionExitByName"
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerCallback2::OnFunctionExitByName
Informe l'objet de profileur que le moteur de script terminée exécution d'un appel de fonction de \(DOM\) de modèle DOM.  
  
## Syntaxe  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### Paramètres  
 `pwszFunctionName`  
 \[in\]  Le nom de la fonction utilisée par le moteur de script est terminé d'exécuter.  
  
 `scriptType`  
 \[in\]  le type de la fonction.  Pour une description des valeurs valides, consultez [PROFILER\_SCRIPT\_TYPE, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## Notes  
 Pour les appels DOM, le moteur de script appelle cette méthode au lieu d'appeler [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md).  Cela est dû à le nombre de seules méthodes et propriétés dans le modèle DOM.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2, interface](../../winscript/reference/iactivescriptprofilercallback2-interface.md)