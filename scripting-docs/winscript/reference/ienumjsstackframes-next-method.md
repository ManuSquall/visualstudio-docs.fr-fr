---
title: "IEnumJsStackFrames::Next, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames::Next, m&#233;thode
Obtient le nombre spécifié de frames.  
  
## Syntaxe  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### Paramètres  
 `cFrameCount`  
 \[in\] Nombre de frames à obtenir.  
  
 `pFrames`  
 \[out\] Tableau pour stocker les frames.  
  
 `pcFetched`  
 \[out\] Nombre de frames retournés.  
  
## Valeur de retour  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IEnumJsStackFrames, interface](../../winscript/reference/ienumjsstackframes-interface.md)