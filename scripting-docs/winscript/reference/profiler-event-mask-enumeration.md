---
title: "Profiler_event_mask, énumération | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68547fcb1fd2cd34b18a3d204baefd24d9da936b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK, énumération
Indique les types d’événements doivent être définis.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Fonctions de profils qui sont définies dans le script d’écrits par l’utilisateur et le code dynamique.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Les profils des fonctions natives qui sont définies par le moteur de script.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Les profils de toutes les fonctions de moteur de script et définis par l’utilisateur, à l’exclusion des appels dans le modèle DOM (Document Object).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Fonctions de profils qui appellent le modèle DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Les profils de toutes les fonctions, y compris les appels dans le DOM.|  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de profils de Script actif, constantes, énumérations et structures](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)