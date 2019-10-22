---
title: Énumération SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574409"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>Énumération SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indique le type d'exception levée. Cette énumération est utilisée par la méthode [IActiveScriptErrorDebug110 :: GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) .  
  
> [!IMPORTANT]
> Ces constantes sont implémentées par la version 11.0 et supérieures de PDM. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Membres  
  
|Membre|valeur|Description|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|L'exception est une exception de première chance.|  
|ETK_USER_UNHANDLED|0x00000001|L'exception n'est pas gérée dans le code utilisateur.|  
|ETK_UNHANDLED|0x00000002|L'exception n'est pas gérée dans le code.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)