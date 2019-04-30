---
title: JsDebugReadMemoryFlags Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830460"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Énumération JsDebugReadMemoryFlags
Indicateurs pour spécifier le comportement pendant la lecture de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indique que l’appelant souhaite que l’opération de lecture réussisse si seule une partie de la mémoire lecture a réussi. S’il est défini, une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS sera être déclenchée uniquement si « Address » n’est pas valide. Si cet indicateur est désactivé, une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS sera déclenchée si une partie de la mémoire demandée était illisible.|  
|`None`|Indique que l’appelant souhaite le comportement par défaut pour ReadMemory.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)