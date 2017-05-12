---
title: "ISimpleConnectionPoint::GetEventCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.GetEventCount
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::GetEventCount"
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::GetEventCount
Retourne le nombre d'événements exposés sur cette interface.  
  
## Syntaxe  
  
```  
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### Paramètres  
 `pulCount`  
 \[out\]  Nombre d'événements exposés sur ce nombre d'interface.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le nombre d'événements exposés sur cette interface.  
  
## Voir aussi  
 [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)