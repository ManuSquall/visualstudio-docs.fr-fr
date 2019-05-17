---
title: Interface ISimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 0d18c8f9eef6ddb1a38473eb19984bd9cf7dbd96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001504"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint, interface
Fournit un moyen simple pour décrire et d’énumérer les événements déclenchés sur un point de connexion particulier. Cette interface facilite également raccorder un `IDispatch` objet à ces événements. Cette interface est implémentée par le Gestionnaire de processus déboguer (PDM) et consommée par les moteurs de script.  
  
 Cette interface est disponible à partir de `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Outre les méthodes héritées de `IUnknown`, le `ISimpleConnectionPoint` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Établit une connexion entre l’objet de point de connexion simple et le récepteur du client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Retourne le DISPID pour chaque événement dans une plage spécifiée d’événements.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Retourne le nombre d’événements affichés sur cette interface.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Met fin à une connexion de notifications précédemment établie par `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)