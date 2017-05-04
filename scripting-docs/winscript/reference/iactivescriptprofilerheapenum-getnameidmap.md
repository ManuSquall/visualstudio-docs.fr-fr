---
title: "IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::GetNameIdMap
Retourne les noms de chaîne correspondant aux valeurs de [PROFILER\_HEAP\_OBJECT\_NAME\_ID, type](../../winscript/reference/profiler-heap-object-name-id-type.md) .  
  
## Syntaxe  
  
```  
HRESULT GetNameIdMap (  
    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],   
    [out] UINT *pcelt);  
```  
  
#### Paramètres  
 `pNameList`  
 \[out\]  Un tableau de noms associés aux valeurs de [PROFILER\_HEAP\_OBJECT\_NAME\_ID, type](../../winscript/reference/profiler-heap-object-name-id-type.md) .  
  
 `pcelt`  
 \[out\]  Le nombre de noms dans le tableau.  
  
## Valeur de retour  
 HRESULT.