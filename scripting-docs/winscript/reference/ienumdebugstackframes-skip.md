---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
Ignore un nombre spécifié de segments dans une séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Nombre de segments de la séquence d'énumération à ignorer.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode ignore un nombre spécifié de segments dans une séquence d'énumération.  
  
## Voir aussi  
 [IEnumDebugStackFrames, interface](../../winscript/reference/ienumdebugstackframes-interface.md)