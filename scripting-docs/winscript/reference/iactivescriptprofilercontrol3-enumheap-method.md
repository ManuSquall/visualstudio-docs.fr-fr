---
title: "IActiveScriptProfilerControl3::EnumHeap, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl3::EnumHeap, m&#233;thode
Retourne une interface \([IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) qui peut être utilisée pour itérer sur les objets heap GC dans le contexte du moteur de script associé.  
  
 Vous pouvez appeler cette méthode de débogage ou libérez mode.  Cette méthode doit être appelée lorsque le thread d'interface utilisateur est inactif.  Une fois que la méthode a été appelée, aucune opération ne doit être exécutée sur le moteur de script à [IActiveScriptProfilerHeapEnum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) jusqu'à ce qu' [IActiveScriptProfilerHeapEnum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) retourne S\_FALSE ou le pointeur d'interface de [IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) est libéré.  
  
## Syntaxe  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Paramètres  
 ppEnum  
 \[out\] Retourne [IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Valeur de retour  
 HRESULT.