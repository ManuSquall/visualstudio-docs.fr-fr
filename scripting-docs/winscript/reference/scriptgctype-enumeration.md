---
title: "SCRIPTGCTYPE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTGCTYPE, &#233;num&#233;ration
Le type de garbage collection à exécuter.  Utilisé dans la méthode [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md).  
  
## Syntaxe  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## Valeurs d'énumération  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|Rendez le garbage collection normal.  La valeur entière est 0.|  
|SCRIPTGCTYPE\_EXHAUSTIVE|Rendez le garbage collection approfondi.  La valeur entière est 1.|  
  
## Voir aussi  
 [Script actif, constantes, énumérations et codes d'erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)