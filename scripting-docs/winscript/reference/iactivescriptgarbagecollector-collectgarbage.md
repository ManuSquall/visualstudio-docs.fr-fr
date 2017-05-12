---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
L'hôte de script actif appelle cette méthode pour démarrer le garbage collection.  
  
## Syntaxe  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### Paramètres  
 `scriptgctype`  
 \[in\]  [SCRIPTGCTYPE, énumération](../../winscript/reference/scriptgctype-enumeration.md) qui spécifie si effectuer un garbage collection normal ou approfondi.  
  
## Valeur de retour  
 Retourne un HRESULT.  
  
## Voir aussi  
 [IActiveScriptGarbageCollector, interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)