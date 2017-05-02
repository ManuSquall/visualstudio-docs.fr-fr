---
title: "IDebugStackFrameSniffer::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSniffer.EnumStackFrames
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSniffer::EnumStackFrames"
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer::EnumStackFrames
Retourne un énumérateur des frames de pile du thread actuel.  
  
## Syntaxe  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Paramètres  
 `ppedsf`  
 \[out\]  Énumérateur des frames de pile du thread actuel.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 L'énumérateur du frame de pile retourne les frames de départ en haut de la pile, en commençant par le frame récemment enfoncé.  
  
## Voir aussi  
 [IDebugStackFrameSniffer, interface](../../winscript/reference/idebugstackframesniffer-interface.md)