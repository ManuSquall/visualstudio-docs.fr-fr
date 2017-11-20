---
title: IEnumDebugExtendedPropertyInfo (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c46815ff1fadd359e3200223dfe9041b6089ad3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>IEnumDebugExtendedPropertyInfo, interface
Énumère les `ExtendedDebugPropertyInfo` structures.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugExtendedPropertyInfo`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Obtient le nombre de `ExtendedDebugPropertyInfo` structures dans un énumérateur.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Récupère un nombre spécifié de `ExtendedDebugPropertyInfo` structures dans une séquence d’énumération.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Ignore un nombre spécifié de `ExtendedDebugPropertyInfo` structures dans une séquence d’énumération.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Réinitialise la séquence d'énumération au début.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structure ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)