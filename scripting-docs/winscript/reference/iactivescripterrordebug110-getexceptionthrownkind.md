---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
Retourne une valeur qui indique le type d'exception levé.  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 \(interface\)](../../winscript/reference/iactivescripterrordebug110-interface.md) est implémenté par la version 11.0 et supérieures de PDM.  Trouvée dans activdbg100.h.  
  
## Syntaxe  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### Paramètres  
 `pExceptionKind`  
 \[out\] Le type d'exception levé \(par exemple, première chance ou non pris en charge\), représenté par une valeur d'énumération [SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND \(énumération\)](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md).  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Voir aussi  
 [IActiveScriptErrorDebug110 \(interface\)](../../winscript/reference/iactivescripterrordebug110-interface.md)