---
title: "IRemoteDebugApplication::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.QueryAlive
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::QueryAlive"
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::QueryAlive
Indique si l'application est sensible.  
  
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
 Cette méthode indique si l'application est sensible.  Les implémentations de cette méthode doivent toujours retourner `S_OK`.  
  
 Si les processus d'application se terminent de façon inattendue, COM retourne une erreur du proxy de marshaling pour les appels à cette méthode.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)