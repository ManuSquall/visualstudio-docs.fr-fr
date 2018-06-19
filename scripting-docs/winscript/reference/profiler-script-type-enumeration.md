---
title: Profiler_script_type, énumération | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734119"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE, énumération
Spécifie le type de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Spécifie le code de script d’écrits par l’utilisateur.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Spécifie le code de script qui est généré dynamiquement pendant l’exécution.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Spécifie le type de script pour les fonctions natives et les objets qui sont définis par le moteur de script.|  
|PROFILER_SCRIPT_TYPE_DOM|Spécifie un appel dans le modèle DOM (Document Object) d’Internet Explorer, par exemple, un appel à la `document.getElementById` (méthode).|  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de profils de Script actif, constantes, énumérations et structures](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)