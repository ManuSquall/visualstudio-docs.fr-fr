---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug::GetRestrictedErrorString"
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Retourne la chaîne d'erreur restreinte par runtime windows, si disponible.  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);  
  
```  
  
#### Paramètres  
 `errorString`  
 \[out\]  la chaîne restreinte d'erreur.  
  
## Voir aussi  
 [IActiveScriptWinRTErrorDebug \(interface\)](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)