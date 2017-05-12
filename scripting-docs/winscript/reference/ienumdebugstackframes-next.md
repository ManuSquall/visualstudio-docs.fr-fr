---
title: "IEnumDebugStackFrames::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Next"
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Next
Récupère un nombre spécifié de segments de la séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de segments à récupérer.  
  
 `prgdsfd`  
 \[out\]  Retourne un tableau d'interfaces d' `DebugStackFrameDescriptor` qui représente les segments sont récupérés.  
  
 `pceltFetched`  
 \[out\]  le nombre réel de segments extraits par l'énumérateur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode extrait un nombre spécifié de segments de la séquence d'énumération.  
  
## Voir aussi  
 [IEnumDebugStackFrames, interface](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor, structure](../../winscript/reference/debugstackframedescriptor-structure.md)