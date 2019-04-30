---
title: Interface IDebugHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979186"
---
# <a name="idebughelper-interface"></a>IDebugHelper, interface
Sert de fabrique pour les explorateurs d’objets et les points de connexion simple. Le Gestionnaire de débogage de processus (PDM) implémente cette interface, qui est consommée par les moteurs de script.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugHelper` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Retourne un Explorateur de propriétés qui encapsule une variante.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Retourne un Explorateur de propriétés qui encapsule une variante et permet la conversion personnalisée de valeurs de type VARIANT ou types VARTYPE en chaînes.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Retourne une interface d’événement qui encapsule une donnée `IDispatch` objet.|