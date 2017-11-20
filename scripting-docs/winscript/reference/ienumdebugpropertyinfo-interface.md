---
title: IEnumDebugPropertyInfo (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61504d60ccb59a0632376bf8e1ef762382b06326
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo, interface
Énumère les `DebugPropertyInfo` structures.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPropertyInfo`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Récupère un nombre spécifié de `DebugPropertyInfo` structures dans une séquence d’énumération.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Ignore un nombre spécifié de `DebugPropertyInfo` structures dans une séquence d’énumération.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Réinitialise la séquence d'énumération au début.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Obtient le nombre de `DebugPropertyInfo` structures dans un énumérateur.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structure DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)