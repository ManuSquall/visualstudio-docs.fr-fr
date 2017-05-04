---
title: "IDebugHelper, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper (interface)"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper, interface
Sert de fabrique aux navigateurs d'objet et aux points de connexion simples.  Le processus de débogage des outils de \(PDM\) de gestionnaire cette interface, qui est consommée par les moteurs de script.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugHelper` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Retourne l'Explorateur de propriétés qui encapsule une VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Retourne l'Explorateur de propriétés qui encapsule une VARIANT, et permet de la conversion personnalisée des valeurs VARIANTES ou des types de VARTYPE aux chaînes.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Retourne une interface d'événement qui encapsule un objet donné d' `IDispatch` .|