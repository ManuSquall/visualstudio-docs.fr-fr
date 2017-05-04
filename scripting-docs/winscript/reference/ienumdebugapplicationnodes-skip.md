---
title: "IEnumDebugApplicationNodes::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Skip
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Skip"
ms.assetid: b2ad1957-95b5-4c09-9a44-5a765a5308ae
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Skip
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
 [IEnumDebugApplicationNodes, interface](../../winscript/reference/ienumdebugapplicationnodes-interface.md)