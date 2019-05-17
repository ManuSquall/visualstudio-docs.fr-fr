---
title: Énumération PROFILER_EVENT_MASK | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7230e65e5559d53e56cf6424a34dd44aa4edda7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831640"
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK, énumération
Indique les types d’événements qui devraient être profilées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Fonctions de profils qui sont définies dans le script écrit par l’utilisateur et de code dynamique.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Les profils des fonctions natives qui sont définies par le moteur de script.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Les profils de toutes les fonctions de moteur de script et définis par l’utilisateur, à l’exclusion des appels dans le modèle DOM (Document Object).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Fonctions de profils qui appellent dans le DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Les profils de toutes les fonctions, y compris les appels dans le DOM.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de Profiler de Script actif, énumérations et structures](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)