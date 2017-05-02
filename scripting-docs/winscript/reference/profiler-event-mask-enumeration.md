---
title: "PROFILER_EVENT_MASK, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PROFILER_EVENT_MASK, &#233;num&#233;ration
Indique les types d'événements qui doivent être profilés.  
  
## Syntaxe  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|PROFILER\_EVENT\_MASK\_TRACE\_SCRIPT\_FUNCTION\_CALL|Fonctions de profilage qui sont définies dans le code écrit par l'utilisateur de script et dynamique.|  
|PROFILER\_EVENT\_MASK\_TRACE\_NATIVE\_FUNCTION\_CALL|Fonctions natives de profils définies par le moteur de script.|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL|Profile toutes les fonctions définies par l'utilisateur et du moteur de script, à l'exclusion de les appels dans le document object model \(DOM\).|  
|PROFILER\_EVENT\_MASK\_TRACE\_DOM\_FUNCTION\_CALL|Les profils fonctionne cet appel dans le modèle DOM.|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL\_WITH\_DOM|Profile toutes les fonctions, y compris les appels dans le modèle DOM.|  
  
## Voir aussi  
 [Profilage de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)