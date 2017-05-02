---
title: "IScriptScriptlet::GetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetEventName"
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IScriptScriptlet::GetEventName
Retourne le nom de l'événement associé au scriptlet.  
  
## Syntaxe  
  
```  
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### Paramètres  
 `pbstr`  
 \[out\]  Une mémoire tampon qui contient le nom de l'événement associé à l'objet d' `IScriptScriptlet` .  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptScriptlet, interface](../../winscript/reference/iscriptscriptlet-interface.md)