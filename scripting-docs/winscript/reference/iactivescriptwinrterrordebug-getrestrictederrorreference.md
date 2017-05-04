---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference"
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
Retourne l'erreur de référence restreinte par runtime windows, si disponible.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### Paramètres  
 `referenceString`  
 \[out\]  la chaîne d'erreur de référence.  
  
## Voir aussi  
 [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)