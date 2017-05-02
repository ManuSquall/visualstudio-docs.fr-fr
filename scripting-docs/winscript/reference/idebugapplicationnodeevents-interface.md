---
title: "IDebugApplicationNodeEvents, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents (interface)"
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents, interface
Fournit l'interface d'événement pour l'interface d' `IDebugApplicationNode` .  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugApplicationNodeEvents` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gère l'événement lorsqu'un nœud enfant est ajouté à un objet de nœud d'application de débogage.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gère l'événement lorsqu'un nœud enfant est supprimé d'un objet de nœud d'application de débogage.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gère un événement ce qui signifie que l'objet de nœud d'application de débogage a été détaché d'un nœud parent.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gère un événement ce qui signifie que l'objet de nœud d'application de débogage a été attaché à un nœud parent.|  
  
## Voir aussi  
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)