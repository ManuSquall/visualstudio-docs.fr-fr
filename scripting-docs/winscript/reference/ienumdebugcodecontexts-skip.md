---
title: "IEnumDebugCodeContexts::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Skip"
ms.assetid: ba917f57-f7a9-419f-96d6-8f4378b12c57
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Skip
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
 [IEnumDebugCodeContexts, interface](../../winscript/reference/ienumdebugcodecontexts-interface.md)