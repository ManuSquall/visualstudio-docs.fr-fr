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
ms.openlocfilehash: 24a93cb3bd230e2489b58d78f6d414ba1df006ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572491"
---
# <a name="idebugextendedproperty-interface"></a>IDebugExtendedProperty, interface
Étend `IDebugProperty` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 En plus des méthodes héritées de `IDebugProperty`, cette interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|Obtient le `ExtendedDebugPropertyInfo` qui décrit ce `IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|Énumère les membres d’une propriété étendue.|  
  
## <a name="requirements"></a>spécifications  
 En-tête : dbgprop. h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)