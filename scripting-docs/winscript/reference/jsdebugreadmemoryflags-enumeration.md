---
title: Énumération JsDebugReadMemoryFlags | Microsoft Docs
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
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571700"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Énumération JsDebugReadMemoryFlags
Indicateurs pour spécifier le comportement pendant la lecture de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Name|Description|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indique que l’appelant souhaite que l’opération de lecture réussisse si seule une partie de la lecture de la mémoire a réussi. Si cette valeur est définie, une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS est déclenchée uniquement si « Address » n’est pas valide. Si cet indicateur est désactivé, une erreur E_JsDEBUG_INVALID_MEMORY_ADDRESS est déclenchée si une partie de la mémoire demandée était illisible.|  
|`None`|Indique que l’appelant souhaite obtenir le comportement par défaut pour ReadMemory (.|  
  
## <a name="requirements"></a>spécifications  
 **En-tête :** jscript9diag. h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)