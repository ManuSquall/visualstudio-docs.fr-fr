---
title: "IDebugCodeContext::SetBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.SetBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::SetBreakPoint"
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::SetBreakPoint
Définit ou espaces libres un point d'arrêt à ce contexte de code.  
  
## Syntaxe  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### Paramètres  
 `bps`  
 \[in\]  Spécifie l'état des points d'arrêt pour ce contexte de code.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode définit ou supprime un point d'arrêt à ce contexte de code.  
  
## Voir aussi  
 [IDebugCodeContext, interface](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT\_STATE, énumération](../../winscript/reference/breakpoint-state-enumeration.md)