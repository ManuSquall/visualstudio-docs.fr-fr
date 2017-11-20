---
title: IDebugProperty (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>IDebugProperty, interface
Utilisé pour décrire une propriété hiérarchique de l’entité en cours de débogage qui a un nom, le type et la valeur. En règle générale, `IDebugProperty` est utilisé pour décrire le résultat de l’évaluation d’expression, une évaluation de l’instruction ou d’évaluation du Registre.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de la `IDebugProperty` Interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Obtenir le `DebugPropertyInfo` qui décrit ce`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Obtient les informations étendues sur une propriété.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Définit la valeur d’une propriété à partir d’une chaîne.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Énumère les membres d’une propriété.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Obtient le parent d’une propriété.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h