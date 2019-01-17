---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e0e9f642e780b745f8b66734893345618a43460
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349818"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
Retourne la fonction SID pour l’erreur d’exécution de Windows, si elle est disponible.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug Interface](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `capabilitySid`  
 La fonctionnalité de SID de l’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)