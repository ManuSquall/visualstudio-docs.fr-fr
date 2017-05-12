---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
Appelé pour informer l'objet de profileur chaque fois que le profilage est arrêté sur un moteur de script.  De cette façon, l'objet de profileur peut appeler ses routines de nettoyage, si nécessaire.  Cette méthode est également appelée par le moteur de script lorsque le moteur de script s'arrête, ou lorsqu'un appel à [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) échoue.  
  
## Syntaxe  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### Paramètres  
 `hrReason`  
 \[in\]  La raison de l'arrêt.  Si le moteur de script s'arrête, `S_OK` est passé.  Si l'appel à [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) retourne un HRESULT d'échec, le HRESULT est passé.  Sinon, cette valeur est extrait d' [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md)