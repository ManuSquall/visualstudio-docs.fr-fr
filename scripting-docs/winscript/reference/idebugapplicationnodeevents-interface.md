---
title: Interface IDebugApplicationNodeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574715"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents, interface
Fournit l’interface d’événement pour l’interface `IDebugApplicationNode`.  
  
 En plus des méthodes héritées de `IUnknown`, l’interface `IDebugApplicationNodeEvents` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gère l’événement lorsqu’un nœud enfant est ajouté à un objet de nœud d’application de débogage.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gère l’événement lorsqu’un nœud enfant est supprimé d’un objet de nœud d’application de débogage.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gère un événement qui signifie que l’objet de nœud d’application de débogage a été détaché d’un nœud parent.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gère un événement qui signifie que l’objet de nœud d’application de débogage a été attaché à un nœud parent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)