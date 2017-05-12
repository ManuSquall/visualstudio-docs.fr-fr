---
title: "IApplicationDebugger::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::QueryAlive"
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::QueryAlive
Indique si le débogueur ne respecte pas.  
  
## Syntaxe  
  
```  
HRESULT QueryAlive();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode indique si le débogueur ne respecte pas.  Les implémentations de cette méthode doivent toujours retourner `S_OK`.  
  
 Si le processus du débogueur s'arrête de façon inattendue, COM retourne une erreur du proxy de marshaling pour les appels à cette méthode.  
  
## Voir aussi  
 [IApplicationDebugger, interface](../../winscript/reference/iapplicationdebugger-interface.md)