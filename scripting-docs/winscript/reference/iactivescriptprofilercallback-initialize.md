---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
Appelé pour initialiser l'objet de profileur chaque fois que le profilage est démarré dans un moteur de script.  
  
## Syntaxe  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### Paramètres  
 `dwContext`  
 \[in\]  Une valeur de 4 octets passé à [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## Valeur de retour  
 Retourne un HRESULT.  Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Si la méthode ne peut pas initialiser l'objet de profileur, elle doit retourner une valeur HRESULT d'échec pour informer le moteur de script.  Dans ce cas, le moteur de script doit appeler directement [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), en passant le HRESULT dans le paramètre, puis récupère l'objet de profileur.  
  
## Voir aussi  
 [IActiveScriptProfilerCallback, interface](../../winscript/reference/iactivescriptprofilercallback-interface.md)