---
title: "IApplicationDebugger::onDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebuggerEvent"
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebuggerEvent
Gère un événement d'application personnalisée.  
  
## Syntaxe  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### Paramètres  
 `riid`  
 \[in\]  L'identificateur d'interface pour l'objet.  
  
 `punk`  
 \[in\]  l'objet événement, qui implémente l'interface a défini par `riid`.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n'est pas actuellement implémentée.|  
  
## Notes  
 La sémantique d' `IUnknown` est entièrement application\/débogueur défini.  
  
 Cette méthode permet des extensions personnalisées du modèle de débogueur ; il n'est pas actuellement implémentée.  
  
 Cette méthode est appelée lorsque `IDebugApplication::FireDebuggerEvent` est appelé.  
  
## Voir aussi  
 [IApplicationDebugger, interface](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)