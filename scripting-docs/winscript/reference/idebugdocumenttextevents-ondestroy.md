---
title: "IDebugDocumentTextEvents::onDestroy | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onDestroy
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onDestroy"
ms.assetid: 1b7eb341-6bad-403f-9821-19112f8732f3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onDestroy
Indique que le document sous\-jacent a perdu et n'est plus valide.  
  
## Syntaxe  
  
```  
HRESULT onDestroy();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode indique que le document sous\-jacent a perdu et n'est plus valide.  
  
## Voir aussi  
 [IDebugDocumentTextEvents, interface](../../winscript/reference/idebugdocumenttextevents-interface.md)