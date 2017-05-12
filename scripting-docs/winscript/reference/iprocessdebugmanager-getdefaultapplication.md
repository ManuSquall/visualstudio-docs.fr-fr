---
title: "IProcessDebugManager::GetDefaultApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::GetDefaultApplication"
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::GetDefaultApplication
Retourne un objet par défaut d'application pour le processus actuel.  
  
## Syntaxe  
  
```  
HRESULT GetDefaultApplication(  
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
 Cette méthode crée un débogage l'objet de l'application et l'ajouter à la liste d'application active, si nécessaire.  
  
 Les moteurs de langage doivent utiliser l'application spécifiée par la méthode d' `GetDefaultApplication` s'ils s'exécutent sur un hôte qui ne fournit aucune application.  
  
## Voir aussi  
 [IProcessDebugManager, interface](../../winscript/reference/iprocessdebugmanager-interface.md)