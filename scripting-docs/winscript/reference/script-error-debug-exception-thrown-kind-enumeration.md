---
title: "Énumération SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Énumération SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indique le type d'exception levée. Cette énumération est utilisée par le [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) (méthode).  
  
> [!IMPORTANT]
>  Ces constantes sont implémentées par la version 11.0 et supérieures de PDM. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Valeur|Description|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|L'exception est une exception de première chance.|  
|ETK_USER_UNHANDLED|0x00000001|L'exception n'est pas gérée dans le code utilisateur.|  
|ETK_UNHANDLED|0x00000002|L'exception n'est pas gérée dans le code.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)