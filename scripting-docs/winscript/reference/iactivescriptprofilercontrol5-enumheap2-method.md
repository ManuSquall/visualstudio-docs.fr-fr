---
title: "IActiveScriptProfilerControl5::EnumHeap2, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerControl5::EnumHeap2, m&#233;thode
Retourne une interface \([IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) qui peut être utilisée pour itérer les objets de tas du Garbage Collection dans le contexte du moteur de script associé.  
  
 Vous pouvez appeler cette méthode en mode debug ou release.  Cette méthode doit être appelée lorsque le thread d'interface utilisateur est inactif.  Une fois la méthode appelée, aucune opération ne doit être exécutée sur le moteur de script sauf [IActiveScriptProfilerHeapEnum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) jusqu'à ce que [IActiveScriptProfilerHeapEnum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) retourne S\_FALSE ou que le pointeur d'interface [IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) soit libéré.  
  
## Syntaxe  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Paramètres  
 enumFlags  
 Valeur qui spécifie si les informations supplémentaires à propos d'un objet désigné dans une relation entre objets sont exposées.  Des informations supplémentaire peuvent indiquer si l'objet pointé est une méthode getter ou setter.  Pour plus d'informations, consultez [PROFILER\_HEAP\_OBJECT\_FLAGS, énumération](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 \[out\] Retourne [IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Valeur de retour  
 Retourne un HRESULT.  Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|L'énumération de tas effectuée correctement.|  
|`E_OUTOFMEMORY`|Il n'y a pas assez de mémoire libre pour effectuer l'énumération du tas.|  
|`E_FAIL`|Une erreur interne s'est produite.|