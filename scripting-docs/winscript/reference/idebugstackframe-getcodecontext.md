---
title: "IDebugStackFrame::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetCodeContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetCodeContext"
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetCodeContext
Retourne le contexte de code actuel associé au frame de pile.  
  
## Syntaxe  
  
```  
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### Paramètres  
 `ppcc`  
 \[out\]  Le contexte de code associé au frame de pile.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le contexte de code actuel associé au frame de pile.  
  
## Voir aussi  
 [IDebugStackFrame, interface](../../winscript/reference/idebugstackframe-interface.md)