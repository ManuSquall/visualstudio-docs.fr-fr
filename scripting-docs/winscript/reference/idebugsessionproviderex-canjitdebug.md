---
title: "IDebugSessionProviderEx:CanJITDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:CanJITDebug
apilocation: scrobj.dll
ms.assetid: 68f91bed-ca69-46b5-b517-ca9ca80b8803
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugSessionProviderEx:CanJITDebug
Détermine si un processus spécifié peut être débogué avec le débogage juste\-à\-temps.  
  
## Syntaxe  
  
```  
HRESULT CanJITDebug(  
   DWORD  pid  
);  
```  
  
#### Paramètres  
 `pid`  
 \[in\]  L'identificateur de processus pour le processus est débogué.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IDebugSessionProviderEx, interface](../../winscript/reference/idebugsessionproviderex-interface.md)