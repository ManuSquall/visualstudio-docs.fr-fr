---
title: Énumération JsDebugReadMemoryFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef1f16ebcf678452f2fe4b0df3ade6350120f05
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094027"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)