---
title: "ISimpleConnectionPoint, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint (interface)"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint, interface
Offre un moyen simple pour décrire et énumérer les événements déclenchés sur le point de connexion spécifique.  Cette interface rend également facile à connecter un objet d' `IDispatch` à ces événements.  Cette interface est implémentée par Process Debug Manager \(PDM\), et consommée par les moteurs de script.  
  
 Cette interface est disponible dans `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `ISimpleConnectionPoint` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Établit une connexion entre l'objet simple de point de connexion et le récepteur du client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Retourne le DISPID et le nom de chaque événement dans une plage spécifiée des événements.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Retourne le nombre d'événements exposés sur cette interface.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Arrête une connexion de notifications précédemment établie par le biais de `ISimpleConnectionPoint::Advise`.|  
  
## Voir aussi  
 [IDebugProperty, interface](../../winscript/reference/idebugproperty-interface.md)