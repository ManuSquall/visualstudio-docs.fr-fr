---
title: ISimpleConnectionPoint (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733909"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint, interface
Fournit un moyen simple pour décrire et de l’énumération des événements déclenchés sur un point de connexion particulier. Cette interface facilite également raccorder un `IDispatch` objet à ces événements. Cette interface est implémentée par le Gestionnaire de processus déboguer (PDM) et consommée par les moteurs de script.  
  
 Cette interface est disponible à partir de `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Outre les méthodes héritées de `IUnknown`, le `ISimpleConnectionPoint` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Établit une connexion entre l’objet de point de connexion simple et le récepteur du client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Retourne le DISPID et le nom de chaque événement dans une plage spécifiée d’événements.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Retourne le nombre d’événements exposés sur cette interface.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Met fin à une connexion de notifications précédemment établie par `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)