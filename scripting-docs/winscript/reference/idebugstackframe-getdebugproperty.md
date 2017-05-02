---
title: "IDebugStackFrame::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDebugProperty"
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDebugProperty
Retourne l'Explorateur de propriétés pour le frame en cours.  
  
## Syntaxe  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### Paramètres  
 `ppDebugProp`  
 \[out\]  Explorateur de propriétés pour le frame en cours.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne l'Explorateur de propriétés pour le frame en cours.  
  
## Voir aussi  
 [IDebugStackFrame, interface](../../winscript/reference/idebugstackframe-interface.md)