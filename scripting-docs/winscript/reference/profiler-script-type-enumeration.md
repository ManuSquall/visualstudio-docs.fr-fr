---
title: "PROFILER_SCRIPT_TYPE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# PROFILER_SCRIPT_TYPE, &#233;num&#233;ration
Spécifie le type de script.  
  
## Syntaxe  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|PROFILER\_SCRIPT\_TYPE\_USER|Spécifie le code de script écrit par l'utilisateur.|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|Spécifie le code de script qui est généré dynamiquement pendant l'exécution.|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|Spécifie le type de script pour les fonctions natives et les objets définis par le moteur de script.|  
|PROFILER\_SCRIPT\_TYPE\_DOM|Spécifie un appel dans le modèle DOM \(DOM\) Internet Explorer, par exemple, un appel à la méthode d' `document.getElementById` .|  
  
## Voir aussi  
 [Profilage de script actif, constantes, énumérations et structures](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)