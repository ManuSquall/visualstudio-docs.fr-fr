---
title: "Énumération JsDebugReadMemoryFlags | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Énumération JsDebugReadMemoryFlags
Indicateurs pour spécifier le comportement pendant la lecture de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indique que l’appelant souhaite que l’opération de lecture pour réussir si une seule partie de la mémoire de lecture a réussi. Si cette option est définie, une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS sera être déclenchée uniquement si « Address » n’est pas valide. Si cet indicateur est désactivée, une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS sera déclenchée si une partie de la mémoire demandée a été illisible.|  
|`None`|Indique que l’appelant souhaite que le comportement par défaut de ReadMemory.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)