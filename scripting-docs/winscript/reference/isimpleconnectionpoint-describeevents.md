---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
Retourne le DISPID et le nom de chaque événement dans une plage spécifiée des événements.  
  
## Syntaxe  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### Paramètres  
 `iEvent`  
 \[in\]  Index du premier événement à récupérer.  
  
 `cEvents`  
 \[in\]  Nombre d'événements à récupérer.  
  
 `prgid`  
 \[out\]  Tableau de valeurs de l'événement DISPID.  
  
 `prgbstr`  
 \[out\]  Choix de noms d'événements.  
  
 `pcEventsFetched`  
 \[out\]  Le nombre réel d'événements récupérés.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`S_FALSE`|Plus d'événements ont été demandés que n'étaient disponibles.  Les événements non disponibles sont représentés avec DISPID\_NULL et BSTR null.|  
|`E_INVALIDARG`|Aucun élément n'a pu être extrait.|  
  
## Notes  
 Cette méthode retourne le DISPID et le nom de chaque événement dans une plage spécifiée des événements.  
  
## Voir aussi  
 [ISimpleConnectionPoint, interface](../../winscript/reference/isimpleconnectionpoint-interface.md)