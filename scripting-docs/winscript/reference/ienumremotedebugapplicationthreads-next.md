---
title: "IEnumRemoteDebugApplicationThreads::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Next"
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Next
La méthode d' `Next` récupère un nombre spécifié de segments de la séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de segments à récupérer.  
  
 `pprdat`  
 \[out\]  Retourne un tableau d'interfaces d' `IRemoteDebugApplicationThread` qui représente les segments sont récupérés.  
  
 `pceltFetched`  
 \[out\]  le nombre réel de segments extraits par l'énumérateur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode extrait un nombre spécifié de segments de la séquence d'énumération.  
  
## Voir aussi  
 [IEnumRemoteDebugApplicationThreads, interface](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)