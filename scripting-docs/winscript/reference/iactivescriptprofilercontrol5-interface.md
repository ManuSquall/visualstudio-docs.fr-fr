---
title: "IActiveScriptProfilerControl5, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptProfilerControl5, interface
Fournit une méthode qui permet d'énumérer les objets de tas du Garbage Collection associés à un moteur de script.  
  
## Syntaxe  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## Méthodes  
 [IActiveScriptProfilerControl5::EnumHeap2, méthode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Retourne une interface \([IActiveScriptProfilerHeapEnum, interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) qui peut être utilisée pour itérer les objets de tas du Garbage Collection dans le contexte du moteur de script associé.