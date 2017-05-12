---
title: "IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetCapabilitySid"
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetCapabilitySid
Retourne la capacité SID pour une erreur d'exécution windows, si disponible.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### Paramètres  
 `capabilitySid`  
 La capacité SID de l'erreur.  
  
## Voir aussi  
 [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)