---
title: "IEnumDebugApplicationNodes::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Next"
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Next
Récupère un nombre spécifié de segments de la séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de segments à récupérer.  
  
 `pprddp`  
 \[out\]  Retourne un tableau d'interfaces d' `IDebugApplicationNode` qui représente les segments sont récupérés.  
  
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
 [IEnumDebugApplicationNodes, interface](../../winscript/reference/ienumdebugapplicationnodes-interface.md)