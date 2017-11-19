---
title: IRemoteDebugApplication110::SetDebuggerOptions | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16782329de6268b309710e60e707d629fd9929a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Appelé pour mettre à jour les options du débogueur. Cette méthode doit être appelée après [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). Le [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) méthode rétablit automatiquement les options par défaut. L’options par défaut, 0 (SDO_NONE).  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication (Interface)](../../winscript/reference/iremotedebugapplication-interface.md) est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mask`  
 Le [énumération SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) masque.  
  
 `value`  
 Le [énumération SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplication (Interface)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interface IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)