---
title: Interface IDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e5e5274e8a3d1c81ce010afc3893b27510a0fad
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348358"
---
# <a name="idebugproperty-interface"></a>IDebugProperty, interface
Utilisé pour décrire n’importe quelle propriété hiérarchique de l’entité en cours de débogage qui a un nom, le type et la valeur. En règle générale, `IDebugProperty` est utilisé pour décrire le résultat de l’évaluation d’expression, une évaluation de l’instruction ou d’évaluation du Registre.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de la `IDebugProperty` Interface.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Obtenir le `DebugPropertyInfo` qui décrit ce `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Obtient les informations étendues sur une propriété.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Définit la valeur d’une propriété à partir d’une chaîne.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Énumère les membres d’une propriété.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Obtient le parent d’une propriété.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h