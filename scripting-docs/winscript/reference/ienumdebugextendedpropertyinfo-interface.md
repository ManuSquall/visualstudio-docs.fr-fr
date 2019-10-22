---
title: Interface IEnumDebugExtendedPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ceae13f2a785a0920598fa79b237a9c8ae1da1c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568930"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>IEnumDebugExtendedPropertyInfo, interface
Énumère les structures de `ExtendedDebugPropertyInfo`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugExtendedPropertyInfo`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Obtient le nombre de structures de `ExtendedDebugPropertyInfo` dans un énumérateur.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Récupère un nombre spécifié de structures de `ExtendedDebugPropertyInfo` dans une séquence d’énumération.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Ignore un nombre spécifié de structures de `ExtendedDebugPropertyInfo` dans une séquence d’énumération.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Réinitialise la séquence d'énumération au début.|  
  
## <a name="requirements"></a>spécifications  
 En-tête : dbgprop. h  
  
## <a name="see-also"></a>Voir aussi  
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)