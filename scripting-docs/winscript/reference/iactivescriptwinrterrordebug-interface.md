---
title: "IActiveScriptWinRTErrorDebug (interface) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug (interface)"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug (interface)
Implémentée par le moteur JavaScript pour fournir des fenêtres étendues des informations sur les erreurs d'exécution d'un événement de [BREAKREASON, énumération](../../winscript/reference/breakreason-enumeration.md) .  Vous pouvez effectuer un QueryInterface pour l'obtention d'un objet d' [IActiveScriptError](../../winscript/reference/iactivescripterror.md) .  
  
> [!IMPORTANT]
>  Cette interface est implémentée par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Méthodes  
 L'interface `IActiveScriptWinRTErrorDebug` expose les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Retourne la capacité SID pour une erreur d'exécution windows, si disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Retourne la chaîne restreinte d'exécution de référence d'erreur windows, si disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Retourne la chaîne d'erreur restreinte par runtime windows, si disponible.|