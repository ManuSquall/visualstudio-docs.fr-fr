---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
Informe l'objet de profileur que le moteur de script est compilé un script.  Cette méthode est appelée pour chaque script qui est compilé.  
  
## Syntaxe  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Paramètres  
 `scriptId`  
 \[in\]  ID unique du script qui a été compilé.  Cet ID est assigné par le moteur de script.  
  
 `type`  
 \[in\]  le type du script qui a été compilé.  Les valeurs sont définies dans [PROFILER\_SCRIPT\_TYPE, énumération](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 \[in\]  Si disponible, un pointeur vers une interface d' `IUnknown` que le profileur doit rechercher un pointeur d' [IDebugDocumentContext, interface](../../winscript/reference/idebugdocumentcontext-interface.md) .  Sinon, il sera null.  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## Notes  
 Le moteur de script peut fournir le contexte de le document uniquement si cela est pris en charge par l'hôte.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md)