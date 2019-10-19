---
title: Interface IEnumDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce4f5a114629a473df99b583c77ae7747bcd339
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574190"
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo, interface
Énumère les structures de `DebugPropertyInfo`.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPropertyInfo`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Récupère un nombre spécifié de structures de `DebugPropertyInfo` dans une séquence d’énumération.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Ignore un nombre spécifié de structures de `DebugPropertyInfo` dans une séquence d’énumération.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Réinitialise la séquence d'énumération au début.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Obtient le nombre de structures de `DebugPropertyInfo` dans un énumérateur.|  
  
## <a name="requirements"></a>spécifications  
 En-tête : dbgprop. h  
  
## <a name="see-also"></a>Voir aussi  
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)