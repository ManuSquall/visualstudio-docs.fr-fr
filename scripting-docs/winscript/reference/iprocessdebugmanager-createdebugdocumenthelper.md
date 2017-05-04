---
title: "IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateDebugDocumentHelper"
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateDebugDocumentHelper
Crée un débogage du programme d'assistance de le document pour cette application.  
  
## Syntaxe  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### Paramètres  
 `punkOuter`  
 \[in\]  Si l'objet retourné doit être regroupé, `punkOuter` est un pointeur d'interface vers `IUnknown`de contrôle.  Sinon, il s'agit d'un pointeur null.  
  
 `pddh`  
 \[out\]  l'objet d'assistance de document de débogage pour cette application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode crée un débogage du programme d'assistance de le document pour cette application.  
  
## Voir aussi  
 [IProcessDebugManager, interface](../../winscript/reference/iprocessdebugmanager-interface.md)