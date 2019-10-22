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
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571788"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint, interface
Fournit un moyen simple pour décrire et énumérer les événements déclenchés sur un point de connexion particulier. Cette interface permet également de raccorder facilement un objet `IDispatch` à ces événements. Cette interface est implémentée par le gestionnaire de débogage de processus (PDM) et utilisée par les moteurs de script.  
  
 Cette interface est disponible à partir de `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 En plus des méthodes héritées de `IUnknown`, l’interface `ISimpleConnectionPoint` expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Établit une connexion entre l’objet de point de connexion simple et le récepteur du client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Retourne le DISPID et le nom de chaque événement dans une plage d’événements spécifiée.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Retourne le nombre d’événements exposés sur cette interface.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Met fin à une connexion de notifications précédemment établie par le biais de `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)