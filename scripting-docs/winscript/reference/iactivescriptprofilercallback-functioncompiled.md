---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
Informe l'objet de profileur que le moteur de script a rencontré une fonction lors de la compilation d'un script.  
  
## Syntaxe  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Paramètres  
 `functionId`  
 \[in\]  ID unique de la fonction.  Cet ID est assigné par le moteur de script.  
  
 `scriptId`  
 \[in\]  ID unique du script que la fonction fait partie de.  
  
 `pwszFunctionName`  
 \[in\]  le nom de la fonction, ou null pour une fonction anonyme.  
  
 `pwszFunctionNameHint`  
 \[in\]  Le nom déduit de la fonction, ou null si le moteur de script ne déduit pas de nom.  
  
 `pIDebugDocumentContext`  
 \[in\]  Si disponible, le pointeur vers une interface d' `IUnknown` que le profileur doit rechercher un pointeur d' [IDebugDocumentContext, interface](../../winscript/reference/idebugdocumentcontext-interface.md) .  Sinon, Null.  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## Notes  
 Le moteur de script peut fournir le contexte de le document uniquement si cela est pris en charge par l'hôte.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md)