---
title: "IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::SetFilterForEventSink"
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::SetFilterForEventSink
Définit le filtre sur une implémentation particulière d' [IDebugApplicationNodeEvents, interface](../../winscript/reference/idebugapplicationnodeevents-interface.md) .  Elle permet aux débogueurs de script pour filtrer les nœuds d'application enfants générés par le compilateur afin que le PDM n'envoie plusieurs événements lorsqu'ils sont créés ou supprimés.  Par défaut, tous les nœuds sont envoyés.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md) est implémenté par PDM v10.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT SetFilterForEventSink(  
        [in] DWORD dwCookie,  
        [in] APPLICATION_NODE_EVENT_FILTER filter  
        );  
  
```  
  
#### Paramètres  
 `dwCookie`  
 Le cookie de filtre.  
  
 `filter`  
 Filtre.  
  
## Voir aussi  
 [IDebugApplicationNode100 \(interface\)](../../winscript/reference/idebugapplicationnode100-interface.md)