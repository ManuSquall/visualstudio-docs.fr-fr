---
title: IDebugHelper (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelper-interface"></a>IDebugHelper, interface
Sert de fabrique pour les explorateurs d’objets et les points de connexion simple. Le Gestionnaire de processus de débogage (PDM) implémente cette interface, qui est consommée par les moteurs de script.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugHelper` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Retourne un Explorateur de propriétés qui encapsule une variante.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Retourne un Explorateur de propriétés qui encapsule un VARIANT, permet la conversion personnalisée de valeurs de type VARIANT ou types VARTYPE en chaînes.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Retourne une interface d’événement qui encapsule une donnée `IDispatch` objet.|