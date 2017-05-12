---
title: "IDebugProperty, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty (interface)"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty, interface
Utilisé pour décrire toute propriété hiérarchique de l'entité en cours de débogage qui a un nom, un type, et une valeur.  Le plus souvent, `IDebugProperty` est utilisé pour décrire le résultat de l'évaluation de l'expression, de l'évaluation d'instruction, ou de l'évaluation de registre.  
  
## Méthodes dans l'ordre Vtable  
 Le tableau suivant répertorie les méthodes d'interface d' `IDebugProperty` .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Obtenez `DebugPropertyInfo` qui décrit cette `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Obtient les informations étendues sur une propriété.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Définit la valeur d'une propriété d'une chaîne.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Énumère les membres d'une propriété.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Obtient le parent d'une propriété.|  
  
## Configuration requise  
 En\-tête : dbgprop.h