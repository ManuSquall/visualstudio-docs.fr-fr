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
ms.openlocfilehash: b9dae0161e3337411a56e316e04cf467a1f05e6a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155717"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Énumération SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indique le type d'exception levée. Cette énumération est utilisée par le [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) (méthode).  
  
> [!IMPORTANT]
>  Ces constantes sont implémentées par la version 11.0 et supérieures de PDM. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Value|Description|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|L'exception est une exception de première chance.|  
|ETK_USER_UNHANDLED|0x00000001|L'exception n'est pas gérée dans le code utilisateur.|  
|ETK_UNHANDLED|0x00000002|L'exception n'est pas gérée dans le code.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)