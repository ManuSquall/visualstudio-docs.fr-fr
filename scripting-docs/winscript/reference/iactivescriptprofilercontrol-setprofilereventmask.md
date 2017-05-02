---
title: "IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptProfilerControl::SetProfilerEventMask
Définit un masque de bits 4 octets qui spécifie les types d'événements que le moteur de script doit déclencher.  
  
## Syntaxe  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### Paramètres  
 `dwEventMask`  
 \[in\]  Un masque de bits 4 octets qui spécifie les types d'événements.  Les bits sont définis dans [PROFILER\_EVENT\_MASK, énumération](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## Valeur de retour  
 Retourne un HRESULT.  Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n'est pas activé.|  
  
## Voir aussi  
 [IActiveScriptProfilerControl, interface](../../winscript/reference/iactivescriptprofilercontrol-interface.md)