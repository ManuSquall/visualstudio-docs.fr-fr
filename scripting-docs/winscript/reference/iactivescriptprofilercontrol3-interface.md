---
title: "IActiveScriptProfilerControl3, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerControl3, interface
Fournit une méthode pour énumérer sur les objets heap GC associés à un moteur de script.  
  
## Syntaxe  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## Méthodes  
 [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Retourne une interface \([IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) qui peut être utilisée pour itérer sur les objets heap GC dans le contexte du moteur de script associé.