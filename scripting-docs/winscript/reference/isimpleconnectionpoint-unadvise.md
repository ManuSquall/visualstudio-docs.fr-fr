---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
Arrête une connexion de notifications précédemment établie par le biais de `ISimpleConnectionPoint::Advise`.  
  
## Syntaxe  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### Paramètres  
 `dwCookie`  
 \[in\]  Jeton de la connexion à exécuter, comme retournée d' `ISimpleConnectionPoint::Advise`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Lorsqu'une connexion consultative est terminée, le point de connexion appelle la méthode d' `Release` sur le pointeur qui a été enregistré pour la connexion pendant la méthode d' `ISimpleConnectionPoint::Advise` .  Cet appel inverse `AddRef` qui a été exécuté pendant `ISimpleConnectionPoint::Advise` lorsque le point de connexion appelle `QueryInterface`du récepteur de notifications.  
  
## Voir aussi  
 [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)