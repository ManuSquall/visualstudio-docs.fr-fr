---
title: Interface IDebugExtendedProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedProperty interface
ms.assetid: e92ea064-0d92-44cf-bb9f-abda783d84be
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e042f75cf0ab0d8c4807c0c0db6ce04e8423f9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156201"
---
# <a name="idebugextendedproperty-interface"></a>IDebugExtendedProperty, interface
Étend `IDebugProperty` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de `IDebugProperty`, cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|Obtient le `ExtendedDebugPropertyInfo` qui décrit ce `IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|Énumère les membres d’une propriété étendue.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)