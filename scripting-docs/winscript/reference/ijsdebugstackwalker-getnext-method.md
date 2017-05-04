---
title: "IJsDebugStackWalker::GetNext, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker::GetNext, m&#233;thode
Obtient le frame suivant.  
  
## Syntaxe  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### Paramètres  
 `ppFrame`  
 \[out\] Objet représentant le frame de pile.  
  
## Valeur de retour  
  
## Notes  
 Retourne E\_JsDEBUG\_OUTSIDE\_OF\_VM lorsqu'il ne reste plus de frames de pile à énumérer  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugStackWalker, interface](../../winscript/reference/ijsdebugstackwalker-interface.md)