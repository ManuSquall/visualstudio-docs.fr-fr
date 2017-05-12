---
title: "SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND (&#233;num&#233;ration) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND (&#233;num&#233;ration)
Indique le type d'exception levée.  Cette énumération est utilisée par la méthode [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md).  
  
> [!IMPORTANT]
>  Ces constantes sont implémentées par la version 11.0 et supérieures de PDM.  Trouvée dans activdbg100.h.  
  
## Syntaxe  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|ETK\_FIRST\_CHANCE|0x00000000|L'exception est une exception de première chance.|  
|ETK\_USER\_UNHANDLED|0x00000001|L'exception n'est pas gérée dans le code utilisateur.|  
|ETK\_UNHANDLED|0x00000002|L'exception n'est pas gérée dans le code.|  
  
## Voir aussi  
 [IActiveScriptErrorDebug110 \(interface\)](../../winscript/reference/iactivescripterrordebug110-interface.md)