---
title: "IProcessDebugManager::CreateApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateApplication"
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateApplication
Crée un débogage l'objet application pour cette application.  
  
## Syntaxe  
  
```  
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Paramètres  
 `ppda`  
 \[out\]  L'objet application de débogage pour cette application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 l'objet créé par cette méthode n'a aucun nom et n'est pas ajouté à la liste d'application active.  Utilisez `IProcessDebugManager::AddApplication` pour ajouter l'application de débogage à la liste d'applications.  
  
## Voir aussi  
 [IProcessDebugManager, interface](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)