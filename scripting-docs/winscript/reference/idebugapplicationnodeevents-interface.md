---
title: IDebugApplicationNodeEvents (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents, interface
Fournit l’interface d’événement pour le `IDebugApplicationNode` interface.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugApplicationNodeEvents` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gère l’événement lorsqu’un nœud enfant est ajouté à un objet de nœud d’application de débogage.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gère l’événement lorsqu’un nœud enfant est supprimé d’un objet de nœud d’application de débogage.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gère un événement, ce qui signifie que l’objet de nœud débogage application a été détachée d’un nœud parent.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gère un événement, ce qui signifie que l’objet de nœud débogage application a été attaché à un nœud parent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)