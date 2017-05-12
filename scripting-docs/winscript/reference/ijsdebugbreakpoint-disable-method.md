---
title: "IJsDebugBreakPoint::Disable, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::Disable, m&#233;thode
Désactive le point d'arrêt.  
  
## Syntaxe  
  
```  
HRESULT Disable(void);  
```  
  
## Valeur de retour  
  
## Notes  
 Retourne E\_UNEXPECTED s'il est appelé sur un point d'arrêt supprimé.  Retourne S\_FALSE s'il est appelé sur un point d'arrêt déjà désactivé.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugBreakPoint, interface](../../winscript/reference/ijsdebugbreakpoint-interface.md)