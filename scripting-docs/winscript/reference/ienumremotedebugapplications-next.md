---
title: "IEnumRemoteDebugApplications::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Next"
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Next
La méthode d' `Next` récupère un nombre spécifié de segments de la séquence d'énumération.  
  
## Syntaxe  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### Paramètres  
 `celt`  
 \[in\]  Le nombre de segments à récupérer.  
  
 `ppda`  
 \[out\]  Retourne un tableau d'interfaces d' `IRemoteDebugApplication` qui représente les segments sont récupérés.  
  
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
 [IEnumRemoteDebugApplications, interface](../../winscript/reference/ienumremotedebugapplications-interface.md)