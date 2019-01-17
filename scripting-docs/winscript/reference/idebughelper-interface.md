---
title: Interface IDebugHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ba760dc15cc0a3d3f2f0d80f3a16c5621582bc11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347474"
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