---
title: "IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::SetDebuggerOptions"
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::SetDebuggerOptions
Appelée pour mettre à jour des options de débogueur.  Cette méthode doit être appelée après [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md).  D' [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) de la méthode réinitialise automatiquement aux options par défaut.  La valeur par défaut d'options à 0 \(SDO\_NONE\).  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT SetDebuggerOptions(  
        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,  
        [in] enum SCRIPT_DEBUGGER_OPTIONS value  
    );  
  
```  
  
#### Paramètres  
 `mask`  
 Le masque de [SCRIPT\_DEBUGGER\_OPTIONS \(énumération\)](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 Valeur de [SCRIPT\_DEBUGGER\_OPTIONS \(énumération\)](../../winscript/reference/script-debugger-options-enumeration.md).  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 \(interface\)](../../winscript/reference/iremotedebugapplication110-interface.md)