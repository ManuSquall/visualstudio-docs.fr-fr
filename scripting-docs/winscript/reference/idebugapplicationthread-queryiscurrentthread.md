---
title: "IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::QueryIsCurrentThread"
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::QueryIsCurrentThread
Détermine si ce thread est le thread en cours de exécution.  
  
## Syntaxe  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi et c'est le thread en cours de exécution.|  
|`S_FALSE`|Ce n'est pas le thread en cours de exécution.|  
  
## Notes  
 Cette méthode détermine si ce thread est le thread en cours de exécution.  
  
## Voir aussi  
 [IDebugApplicationThread, interface](../../winscript/reference/idebugapplicationthread-interface.md)