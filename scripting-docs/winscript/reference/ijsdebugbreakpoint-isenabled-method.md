---
title: "IJsDebugBreakPoint::IsEnabled, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::IsEnabled, m&#233;thode
Détermine si le point d'arrêt est activé.  
  
## Syntaxe  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### Paramètres  
 `pIsEnabled`  
 \[out\] Retourne True si le point d'arrêt est activé ; sinon, retourne False.  
  
## Valeur de retour  
  
## Notes  
 Retourne E\_UNEXPECTED s'il est appelé sur un point d'arrêt supprimé.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugBreakPoint, interface](../../winscript/reference/ijsdebugbreakpoint-interface.md)