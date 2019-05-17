---
title: Interface IActiveScriptWinRTErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e7728b4143231912227e5e55faa5eef01b7490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425788"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug (interface)
Implémenté par le moteur JavaScript pour fournir des informations d’erreur étendues Windows Runtime à partir d’un [énumération BREAKREASON](../../winscript/reference/breakreason-enumeration.md) événement. Vous pouvez effectuer une QueryInterface pour l’obtenir à partir d’un [IActiveScriptError](../../winscript/reference/iactivescripterror.md) objet.  
  
> [!IMPORTANT]
> Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IActiveScriptWinRTErrorDebug` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Retourne la fonction SID pour l’erreur d’exécution de Windows, si elle est disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Retourne le Runtime Windows restreint la chaîne de référence d’erreur, s’il est disponible.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Retourne le Runtime Windows restreint la chaîne d’erreur, s’il est disponible.|