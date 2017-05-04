---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
Informe l'objet de profileur que le moteur de script va exécuter un appel de fonction de \(DOM\) de modèle DOM.  
  
## Syntaxe  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### Paramètres  
 `pwszFunctionName`  
 \[in\]  le nom de la fonction que le moteur de script va exécuter.  
  
 `scriptType`  
 \[in\]  le type de la fonction.  Pour une description des valeurs valides, consultez [PROFILER\_SCRIPT\_TYPE, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## Notes  
 Pour les appels DOM, le moteur de script appelle cette méthode au lieu d'appeler [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md).  Cela est dû à le nombre de seules méthodes et propriétés dans le modèle DOM.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2, interface](../../winscript/reference/iactivescriptprofilercallback2-interface.md)