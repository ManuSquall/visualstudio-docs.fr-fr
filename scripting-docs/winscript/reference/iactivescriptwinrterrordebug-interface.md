---
title: IActiveScriptWinRTErrorDebug (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34fcc4f1dc3ebc21f9303ba49f1709f2d023a29a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug (interface)
Implémenté par le moteur JavaScript pour fournir des informations d’erreur étendues Windows Runtime à partir d’un [énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md) événement. Vous pouvez effectuer un QueryInterface pour l’obtenir à partir d’un [IActiveScriptError](../../winscript/reference/iactivescripterror.md) objet.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IActiveScriptWinRTErrorDebug` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Retourne la SID de capacité de l’erreur Windows Runtime, si elle est disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Retourne le Windows Runtime restreint la chaîne de référence d’erreur, s’il est disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Retourne le Windows Runtime restreint la chaîne d’erreur, s’il est disponible.|