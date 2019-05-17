---
title: Interface IEnumDebugExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugExpressionContexts interface
ms.assetid: 1c11f9ff-c5a6-48b8-a287-0d782513ba55
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c257fe12f27bb5e6ffd5835986d0c7cac6193a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807372"
---
# <a name="ienumdebugexpressioncontexts-interface"></a>IEnumDebugExpressionContexts, interface
Énumère une collection d’objets `IDebugExpressionContexts`.  
  
 Outre les méthodes héritées de `IUnknown`, le `IEnumDebugExpressionContexts` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IEnumDebugExpressionContexts::Next](../../winscript/reference/ienumdebugexpressioncontexts-next.md)|Récupère un nombre spécifié de segments dans la séquence d’énumération.|  
|[IEnumDebugExpressionContexts::Skip](../../winscript/reference/ienumdebugexpressioncontexts-skip.md)|Ignore un nombre spécifié de segments dans une séquence d’énumération.|  
|[IEnumDebugExpressionContexts::Reset](../../winscript/reference/ienumdebugexpressioncontexts-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[IEnumDebugExpressionContexts::Clone](../../winscript/reference/ienumdebugexpressioncontexts-clone.md)|Crée un énumérateur qui contient le même état que l’énumérateur en cours.|