---
title: Énumération PROFILER_SCRIPT_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574569"
---
# <a name="profiler_script_type-enumeration"></a>PROFILER_SCRIPT_TYPE, énumération
Spécifie le type de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|PROFILER_SCRIPT_TYPE_USER|Spécifie le code de script écrit par l’utilisateur.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Spécifie le code de script généré de manière dynamique pendant l’exécution.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Spécifie le type de script pour les fonctions natives et les objets définis par le moteur de script.|  
|PROFILER_SCRIPT_TYPE_DOM|Spécifie un appel dans le Document Object Model (DOM) d’Internet Explorer, par exemple, un appel à la méthode `document.getElementById`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes, énumérations et structures actives du profileur de script actif](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerCallback :: ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [IActiveScriptProfilerCallback2 :: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)