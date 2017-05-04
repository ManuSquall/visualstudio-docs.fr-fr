---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
Établit une connexion entre l'objet simple de point de connexion et le récepteur du client.  
  
## Syntaxe  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### Paramètres  
 `pdisp`  
 \[in\]  Pointeur vers l'interface d' `IDispatch` sur le récepteur de notifications du client.  Le récepteur du client reçoit des appels sortants du point de connexion simple.  
  
 `pdwCookie`  
 \[out\]  Pointeur vers un jeton retourné qui identifie cette connexion.  L'appelant utilise ce jeton ultérieurement pour supprimer la connexion en la passant à la méthode d' `ISimpleConnectionPoint::Unadvise` .  Si la connexion n'était pas correctement construite, cette valeur est zéro.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode génère une connexion entre l'objet simple de point de connexion et le récepteur du client.  
  
## Voir aussi  
 [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)